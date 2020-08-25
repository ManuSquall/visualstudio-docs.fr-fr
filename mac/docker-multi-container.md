---
title: Application à conteneurs multiples avec Docker Compose
description: Apprendre à gérer plusieurs conteneurs et communiquer entre eux dans Visual Studio pour Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/03/2020
ms.topic: tutorial
ms.openlocfilehash: 4dd8695ccf8f1fcf13b9b52387d28c68f8812aec
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800721"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Créer une application multiconteneur avec Docker Compose

Dans ce didacticiel, vous allez apprendre à gérer plusieurs conteneurs et communiquer entre eux lorsque vous utilisez Docker Compose dans Visual Studio pour Mac.

## <a name="prerequisites"></a>Prérequis

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio pour Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>Créer une application web ASP.NET Core et ajouter la prise en charge de Docker

1. Créez une solution en accédant à **Fichier > Nouvelle solution**.
1. Sous **Web et Console > application,** choisissez le modèle **application Web** : ![ créer une application ASP.net](media/docker-quickstart-1.png)
1. Sélectionnez le framework cible. Dans cet exemple, nous allons utiliser .NET Core 3,1 : définir la version cible de .NET ![ Framework](media/docker-quickstart-2.png)
1. Entrez les détails du projet, comme le nom du projet (_DockerDemoFrontEnd_ dans cet exemple) et le nom de la solution (_DockerDemo_). Le projet créé contient tous les éléments de base pour générer et exécuter un site web ASP.NET Core.
1. Dans le Panneau Solutions, cliquez avec le bouton droit sur le projet DockerDemoFrontEnd et sélectionnez **ajouter > ajouter prise en charge**de l’ancrage : ![ Ajouter la prise en charge de l’ancrage](media/docker-quickstart-3.png)

Visual Studio pour Mac ajoute automatiquement un nouveau projet appelé **docker-compose** à votre solution et un **Dockerfile** à votre projet existant.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>Créer une API web ASP.NET Core et ajouter la prise en charge de Docker

Ensuite, nous allons créer un deuxième projet qui servira d’API principale. Le modèle **API .NET Core** modèle inclut un contrôleur qui permet de gérer les requêtes RESTful.

1. Ajoutez un nouveau projet à la solution existante en cliquant sur la solution et en choisissant **Ajouter > Ajouter un nouveau projet**.
1. Sous **Web et Console > application,** choisissez le modèle **API** .
1. Sélectionnez le framework cible. Dans cet exemple, nous allons utiliser .NET Core 3,1.
1. Entrez les détails du projet, tels que le nom du projet (_MyWebAPI_ dans cet exemple).
1. Une fois créé, accédez au Panneau Solutions puis cliquez avec le bouton droit sur le projet MyWebAPI et sélectionnez **ajouter > ajouter la prise en charge**de l’ancrage.

Le fichier **docker-compose.yml** dans le projet **docker-compose** sera automatiquement mis à jour pour inclure le projet d’API en plus du projet d’application web existant. Lorsque nous générons et exécutons le projet **docker-compose**, chacun de ces projets est déployé sur un conteneur Docker distinct.

```yaml
version: '3.4'

services:
  dockerdemofrontend:
    image: ${DOCKER_REGISTRY-}dockerdemofrontend
    build:
      context: .
      dockerfile: DockerDemoFrontEnd/Dockerfile

  mywebapi:
    image: ${DOCKER_REGISTRY-}mywebapi
    build:
      context: .
      dockerfile: MyWebAPI/Dockerfile
```

## <a name="integrate-the-two-containers"></a>Intégrer les deux conteneurs

Nous avons maintenant deux projets ASP.NET dans notre solution, et les deux sont configurés avec la prise en charge Docker. Ensuite, nous devons ajouter du code !

1. Dans le `DockerDemoFrontEnd` projet, ouvrez le fichier *pages/index. cshtml. cs* et remplacez la `OnGet` méthode par le code suivant :

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://mywebapi/WeatherForecast");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > Dans le code de production, vous ne devez pas supprimer `HttpClient` après chaque demande. Pour connaître les meilleures pratiques, consultez [utiliser HttpClientFactory pour implémenter des demandes http résilientes](https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

1. Dans le fichier *Index.cshtml*, ajoutez une ligne pour afficher `ViewData["Message"]` afin que le fichier ressemble à ce qui suit :

      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }

      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```
  
1. Dans les projets de serveur frontal et d’API Web, commentez l’appel à [Microsoft. AspNetCore. Builder. HttpsPolicyBuilderExtensions. UseHttpsRedirection](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.builder.httpspolicybuilderextensions.usehttpsredirection) dans la `Configure` méthode de *Startup.cs*, car cet exemple de code utilise http, et non HTTPS, pour appeler l’API Web.

      ```csharp
                  //app.UseHttpsRedirection();
      ```

1. Définissez le projet `docker-compose` comme projet de démarrage et accédez à **Exécuter > Démarrer le débogage**. Si tout est correctement configuré, vous voyez le message « Hello from webfrontend and webapi (with value 1). » :

![Solution Docker à plusieurs conteneurs en cours d’exécution](media/docker-multicontainer-debug.png)
