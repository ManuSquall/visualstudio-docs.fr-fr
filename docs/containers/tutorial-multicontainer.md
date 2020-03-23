---
title: Tutoriel multicontainer utilisant Docker Compose & ASP.NET Core
author: ghogen
description: Apprenez à utiliser plusieurs conteneurs avec Docker Compose
ms.author: ghogen
ms.date: 01/10/2020
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: b9e1a2fc7c9027c34aeb8a0e0d1d44fdb0211e65
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027332"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Tutorial: Créer une application multi-conteneurs avec Docker Compose

Dans ce tutoriel, vous apprendrez à gérer plus d’un conteneur et à communiquer entre eux lors de l’utilisation d’outils conteneurs dans Visual Studio.  La gestion de plusieurs conteneurs nécessite une *orchestration de conteneurs* et nécessite un orchestrateur tel que Docker Compose, Kubernetes ou Service Fabric. Ici, nous allons utiliser Docker Compose. Docker Compose est idéal pour le débogage local et les tests au cours du cycle de développement.

## <a name="prerequisites"></a>Conditions préalables requises

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) avec le **Développement Web**, la charge de travail **Azure Tools,** ou la charge de travail **de développement multiplateforme .NET Core** installée
::: moniker-end

::: moniker range=">= vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) avec la charge de travail **Développement web**, **Outils Azure** et/ou la charge de travail **Développement multiplateforme .NET Core** installée
* [Outils de développement .NET core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) pour le développement avec .NET Core 2.2
* [.NET Core 3 Outils de développement](https://dotnet.microsoft.com/download/dotnet-core/3.1) pour le développement avec .NET Core 3.1.
::: moniker-end

## <a name="create-a-web-application-project"></a>Créer un projet d’application Web

Dans Visual Studio, créez un projet ASP.NET Core `WebFrontEnd`Web **Application,** nommé . Sélectionnez **l’application Web** pour créer une application web avec des pages Razor. 
  
::: moniker range="vs-2017"

Ne sélectionnez pas**Activer la prise en charge de Docker**. Vous ajouterez le soutien de Docker plus tard.

![Capture d’écran de la création du projet web](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Capture d’écran de la création du projet web](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project1.png)

Ne sélectionnez pas**Activer la prise en charge de Docker**. Vous ajouterez le soutien de Docker plus tard.

![Capture d’écran de la création du projet web](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Créer un projet d’API Web

Ajoutez un projet à la même solution et appelez-le *MyWebAPI*. Sélectionnez **l’API** comme type de projet, et effacer la case à cocher pour **Configurer pour HTTPS**. Dans cette conception, nous utilisons seulement SSL pour la communication avec le client, pas pour la communication entre les conteneurs dans la même application web. Seul `WebFrontEnd` il n’a besoin que de HTTPS et le code dans les exemples suppose que vous avez effacé cette case à cocher.

::: moniker range="vs-2017"
   ![Capture d’écran de la création du projet Web API](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Capture d’écran de la création du projet Web API](./media/tutorial-multicontainer/vs-2019/web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Ajouter du code pour appeler l’API Web

1. Dans `WebFrontEnd` le projet, ouvrez le *fichier* Index.cshtml.cs `OnGet` et remplacez la méthode par le code suivant.

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
    > Dans le code du monde réel, vous ne devriez pas disposer `HttpClient` après chaque demande. Pour les meilleures pratiques, voir [Utilisez HttpClientFactory pour mettre en œuvre des demandes HTTP résilientes](https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

   Pour .NET Core 3.1 dans Visual Studio 2019 ou plus tard, le modèle Web API utilise une API WeatherForecast, donc uncomment cette ligne et commenter la ligne pour ASP.NET 2.x.

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

1. (ASP.NET 2.x seulement) Maintenant, dans le projet Web API, ajoutez du code au contrôleur des valeurs pour personnaliser le message retourné par l’API pour l’appel que vous avez ajouté à partir de *webfrontend*.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    Avec .NET Core 3.1, vous n’en avez pas besoin, car vous pouvez utiliser l’API WeatherForecast qui est déjà là. Cependant, vous devez commenter l’appel à <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> la `Configure` méthode dans *Startup.cs*, parce que ce code utilise HTTP, pas HTTPS, pour appeler l’API Web.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. Dans `WebFrontEnd` le projet, choisissez **Ajouter > Support Orchestrateur de conteneurs**. Le dialogue **Docker Support Options** apparaît.

1. Choisissez **Docker Compose**.

1. Choisissez votre système d’exploitation cible, par exemple, Linux.

   ![Capture d’écran du choix du système d’exploitation cible](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio crée un fichier *docker-compose.yml* et un fichier *.dockerignore* dans le nœud **docker-compose** dans la solution, et ce projet montre en police boldface, ce qui montre que c’est le projet de démarrage.

   ![Capture d’écran de Solution Explorer avec docker-compose projet ajouté](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   Le *docker-compose.yml* apparaît comme suit:

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   Le fichier *.dockerignore* contient des types de fichiers et des extensions que vous ne voulez pas que Docker inclue dans le conteneur. Ces fichiers sont généralement associés à l’environnement de développement et au contrôle des sources, et ne font pas partie de l’application ou du service que vous développez.

   Regardez la section **Outils de conteneurs** de la vitre pour plus de détails sur les commandes exécutées.  Vous pouvez voir l’outil de commande docker-compose est utilisé pour configurer et créer les conteneurs de temps d’exécution.

1. Dans le projet Web API, encore une fois à droite cliquez sur le nœud de projet, et choisissez **Add** > **Container Orchestrator Support**. Choisissez **Docker Compose,** puis sélectionnez le même système d’exploitation cible.  

    > [!NOTE]
    > Dans cette étape, Visual Studio proposera de créer un Dockerfile. Si vous faites cela sur un projet qui a déjà le soutien Docker, vous êtes invité si vous voulez remplacer le Dockerfile existant. Si vous avez apporté des modifications à votre Dockerfile que vous souhaitez conserver, choisissez non.

    Visual Studio apporte quelques modifications à votre docker composer fichier YML. Maintenant, les deux services sont inclus.

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

1. Exécutez le site localement maintenant (F5 ou Ctrl-F5) pour vérifier qu’il fonctionne comme prévu. Si tout est configuré correctement avec la version .NET Core 2.x, vous voyez le message "Bonjour de webfrontend et webapi (avec la valeur 1)."  Avec .NET Core 3, vous voyez les données de prévisions météorologiques.

   Le premier projet que vous utilisez lorsque vous ajoutez l’orchestration de conteneurs est configuré pour être lancé lorsque vous exécutez ou déboguer. Vous pouvez configurer l’action de lancement dans les **propriétés du projet** pour le projet docker-compose.  Sur le nœud de projet docker-compose, cliquez à droite pour ouvrir le menu contextuelle, puis choisissez **Propriétés,** ou utilisez Alt-Enter.  La capture d’écran suivante montre les propriétés que vous souhaitez pour la solution utilisée ici.  Par exemple, vous pouvez modifier la page chargée en personnalisant la propriété **URL du Service.**

   ![Capture d’écran des propriétés du projet docker-compose](media/tutorial-multicontainer/launch-action.png)

   Voici ce que vous voyez lors du lancement (la version .NET Core 2.x):

   ![Capture d’écran de l’application web en cours d’exécution](media/tutorial-multicontainer/webfrontend.png)

   L’application web pour .NET 3.1 affiche les données météorologiques en format JSON.

## <a name="next-steps"></a>Étapes suivantes

Regardez les options pour déployer vos [conteneurs à Azure](/azure/containers).

## <a name="see-also"></a>Voir aussi
  
[Docker Compose](https://docs.docker.com/compose/)  
[Outils de conteneurs](/visualstudio/containers/)
