---
title: Utiliser plusieurs conteneurs à l’aide de Docker Compose
author: ghogen
description: Découvrez comment utiliser plusieurs conteneurs avec Docker Compose
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 03/15/2021
ms.technology: vs-azure
ms.topic: tutorial
ms.openlocfilehash: 43684288eea2e1864bf31a8bb68bbac1b217a976
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973276"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Didacticiel : Créer une application multiconteneur avec Docker Compose

Dans ce didacticiel, vous allez apprendre à gérer plusieurs conteneurs et à communiquer entre eux quand vous utilisez des outils de conteneur dans Visual Studio.  La gestion de plusieurs conteneurs nécessite l' *orchestration de conteneur* et nécessite un orchestrateur, comme docker compose, Kubernetes ou service fabric. Ici, nous allons utiliser Docker Compose. Docker Compose est idéal pour le débogage et les tests locaux au cours du cycle de développement.

## <a name="prerequisites"></a>Prérequis

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) avec le **développement Web**, la charge de travail **Azure Tools** ou la charge de travail de **développement multiplateforme .net Core** installée
::: moniker-end

::: moniker range=">= vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) avec la charge de travail **Développement web**, **Outils Azure** et/ou la charge de travail **Développement multiplateforme .NET Core** installée
* [Outils de développement .NET core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) pour le développement avec .NET Core 2.2
* [Outils de développement .net Core 3](https://dotnet.microsoft.com/download/dotnet-core/3.1) pour le développement avec .net Core 3,1.
::: moniker-end

## <a name="create-a-web-application-project"></a>Créer un projet d’application Web

Dans Visual Studio, créez un projet d’application **web ASP.net Core** , nommé `WebFrontEnd` , pour créer une application Web avec les pages Razor.
  
::: moniker range="vs-2017"

Ne sélectionnez pas **Activer la prise en charge de Docker**. Vous ajouterez la prise en charge de l’ancrage ultérieurement.

![Capture d’écran de la création du projet Web](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Créer ASP.NET Core projet d’application Web](./media/tutorial-multicontainer/vs-2019/create-web-project1.png)

Ne sélectionnez pas **Activer la prise en charge de Docker**. Vous ajouterez la prise en charge de l’ancrage ultérieurement.

![Capture d’écran de l’écran d’informations supplémentaires lors de la création d’un projet Web. L’option permettant d’activer la prise en charge de l’ancrage n’est pas sélectionnée.](./media/tutorial-multicontainer/vs-2019/create-web-project-additional-information.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Créer un projet d’API Web

Ajoutez un projet à la même solution et appelez-le *MyWebAPI*. Sélectionnez **API** comme type de projet, puis désactivez la case à cocher **configurer pour HTTPS**. Dans cette conception, nous utilisons uniquement SSL pour la communication avec le client, et non pour la communication entre les conteneurs dans la même application Web. `WebFrontEnd`Nécessite uniquement https et le code dans les exemples part du principe que vous avez désactivé cette case à cocher. En général, les certificats de développeur .NET utilisés par Visual Studio sont uniquement pris en charge pour les requêtes externes à des conteneurs, et non pour les demandes de conteneur à conteneur.

::: moniker range="vs-2017"
   ![Capture d’écran de la création du projet d’API Web](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Capture d’écran de la création du projet d’API Web](./media/tutorial-multicontainer/vs-2019/create-webapi-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Ajouter du code pour appeler l’API Web

1. Dans le `WebFrontEnd` projet, ouvrez le fichier *index. cshtml. cs* et remplacez la `OnGet` méthode par le code suivant.

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          // request.RequestUri = new Uri("http://mywebapi/WeatherForecast"); // ASP.NET 3 (VS 2019 only)
          request.RequestUri = new Uri("http://mywebapi/api/values/1"); // ASP.NET 2.x
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > Dans le code réel, vous ne devez pas supprimer `HttpClient` après chaque demande. Pour connaître les meilleures pratiques, consultez [utiliser HttpClientFactory pour implémenter des demandes http résilientes](/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

   Pour .NET Core 3,1 dans Visual Studio 2019 ou version ultérieure, le modèle d’API Web utilise une API WeatherForecast. par conséquent, supprimez les marques de commentaire de la ligne et commentez la ligne pour ASP.NET 2. x.

1. Dans le fichier *Index.cshtml*, ajoutez une ligne pour afficher `ViewData["Message"]` afin que le fichier ressemble à ce qui suit :
    
      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }
    
      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```

1. (ASP.NETd 2. x uniquement) Maintenant, dans le projet d’API Web, ajoutez du code au contrôleur de valeurs pour personnaliser le message retourné par l’API pour l’appel que vous avez ajouté à partir de *WebFrontEnd*.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    Avec .NET Core 3,1, vous n’avez pas besoin de cela, car vous pouvez utiliser l’API WeatherForecast qui est déjà présente. Toutefois, vous devez commenter l’appel à <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*>  dans la `Configure` méthode dans *Startup. cs*, car ce code utilise HTTP, et non HTTPS, pour appeler l’API Web.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. Dans le `WebFrontEnd` projet, choisissez **Ajouter > prise en charge d’Orchestrator de conteneur**. La boîte de dialogue **options de prise en charge** de l’ancrage s’affiche.

1. Choisissez **docker compose**.

1. Choisissez votre système d’exploitation cible, par exemple Linux.

   ![Capture d’écran du choix du système d’exploitation cible](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio crée un fichier *docker-compose. yml* et un fichier *. dockerignore* dans le nœud **dockr-compose** de la solution, et ce projet s’affiche en caractères gras, ce qui indique qu’il s’agit du projet de démarrage.

   ![Capture d’écran de Explorateur de solutions avec le projet d’ancrage-compose ajouté](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   *Docker-compose. yml* se présente comme suit :

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   Le fichier *. dockerignore* contient des types de fichiers et des extensions que vous ne souhaitez pas inclure dans le conteneur par l’ancrage. Ces fichiers sont généralement associés à l’environnement de développement et au contrôle de code source, et non à l’application ou au service que vous développez.

   Examinez la section **outils de conteneur** du volet de sortie pour plus d’informations sur les commandes en cours d’exécution.  Vous pouvez voir l’outil en ligne de commande dockr-compose est utilisé pour configurer et créer les conteneurs du Runtime.

1. Dans le projet d’API Web, cliquez à nouveau avec le bouton droit sur le nœud du projet, puis sélectionnez **Ajouter** la  >  **prise en charge de Container Orchestrator**. Choisissez **docker compose**, puis sélectionnez le même système d’exploitation cible.  

    > [!NOTE]
    > Dans cette étape, Visual Studio propose de créer un fichier dockerfile. Si vous effectuez cette opération sur un projet qui dispose déjà de la prise en charge de l’ancrage, vous êtes invité à indiquer si vous souhaitez remplacer le fichier dockerfile existant. Si vous avez apporté des modifications à vos fichier dockerfile que vous souhaitez conserver, choisissez non.

    Visual Studio apporte des modifications à votre fichier YML compose. Désormais, les deux services sont inclus.

    ```yaml
    version: '3.4'
    
    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
    
      mywebapi:
        image: ${DOCKER_REGISTRY-}mywebapi
        build:
          context: .
          dockerfile: MyWebAPI/Dockerfile
    ```

1. Exécutez le site localement maintenant (F5 ou CTRL + F5) pour vérifier qu’il fonctionne comme prévu. Si tout est configuré correctement avec la version .NET Core 2. x, le message « Hello from WebFrontEnd and WebAPI (avec la valeur 1) » s’affiche.  Avec .NET Core 3, vous voyez des données de prévisions météorologiques.

   Le premier projet que vous utilisez lorsque vous ajoutez une orchestration de conteneur est configuré pour être lancé lorsque vous exécutez ou déboguez. Vous pouvez configurer l’action de lancement dans les **Propriétés du projet** pour le projet dockr-compose.  Sur le nœud du projet dockr-compose, cliquez avec le bouton droit pour ouvrir le menu contextuel, puis choisissez **Propriétés** ou utilisez ALT + ENTRÉE.  La capture d’écran suivante montre les propriétés que vous souhaiteriez pour la solution utilisée ici.  Par exemple, vous pouvez modifier la page qui est chargée en personnalisant la propriété **URL du service** .

   ![Capture d’écran des propriétés du projet dockr-compose](media/tutorial-multicontainer/launch-action.png)

   Voici ce que vous voyez quand vous lancez (la version .NET Core 2. x) :

   ![Capture d’écran de l’exécution de l’application Web](media/tutorial-multicontainer/webfrontend.png)

   L’application Web pour .NET 3,1 affiche les données météorologiques au format JSON.

## <a name="next-steps"></a>Étapes suivantes

Examinez les options de déploiement de vos [conteneurs sur Azure](/azure/containers).

Pour mieux contrôler les services qui sont démarrés au cours d’une session de débogage, Découvrez comment utiliser Docker Compose profils de lancement pour configurer les services qui s’exécutent lors du débogage. Consultez [gérer les profils de lancement pour docker compose](launch-profiles.md)

## <a name="see-also"></a>Voir aussi
  
[Docker Compose](https://docs.docker.com/compose/)  
[Outils de conteneur](./index.yml)