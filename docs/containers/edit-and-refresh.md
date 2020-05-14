---
title: Applications Debug dans un conteneur Docker local ( Microsoft Docs
description: Apprenez à modifier une application qui fonctionne dans un conteneur Docker local, rafraîchissez le conteneur via Edit et Refresh, puis définissez les points d’arrêt de débogage.
ms.author: ghogen
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: conceptual
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 9f1d80d540e9a25a3ef62ee0819c6f6655b9b3ab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75916521"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Applications Debug dans un conteneur Docker local

Visual Studio offre un moyen cohérent de développer des conteneurs Docker et de valider votre application localement. Vous pouvez exécuter et déboguer vos applications dans des conteneurs Linux ou Windows fonctionnant sur votre bureau Windows local avec Docker installé, et vous n’avez pas à redémarrer le conteneur chaque fois que vous effectuez un changement de code.

Cet article illustre comment utiliser Visual Studio pour démarrer une application dans un conteneur Docker local, apporter des modifications, puis rafraîchir le navigateur pour voir les modifications. Cet article vous montre également comment définir des points d’arrêt pour le débogage pour les applications conteneurisées. Les types de projets pris en charge comprennent les applications Web et consoles .NET Core et .NET Core. Dans cet article, nous utilisons ASP.NET applications Web Core et .NET Framework console apps.

Si vous avez déjà un projet de type pris en charge, Visual Studio peut créer un Dockerfile et configurer votre projet pour fonctionner dans un conteneur. Voir [Container Tools in Visual Studio](overview.md).

## <a name="prerequisites"></a>Conditions préalables requises

Pour déboiffer les applications dans un conteneur Docker local, les outils suivants doivent être installés :

::: moniker range="vs-2017"

* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) avec la charge de travail web Développement installée

::: moniker-end

::: moniker range="vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) avec la charge de travail web Développement installé

::: moniker-end

Pour gérer des conteneurs Docker localement, vous devez avoir un client Docker local. Vous pouvez utiliser la [boîte à outils Docker](https://www.docker.com/products/docker-toolbox), qui nécessite Hyper-V pour être désactivé. Vous pouvez également utiliser [Docker pour Windows](https://www.docker.com/get-docker), qui utilise Hyper-V et nécessite Windows 10.

Les conteneurs Docker sont disponibles pour les projets .NET Framework et .NET Core. Examinons ces deux exemples. Tout d’abord, nous regardons une application web .NET Core. Ensuite, nous regardons une application de console cadre .NET.

## <a name="create-a-web-app"></a>Créer une application web

Si vous avez un projet et que vous avez ajouté le support Docker tel que décrit dans la [vue d’ensemble,](overview.md)sautez cette section.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Modifier votre code et actualiser

Pour itérer rapidement les modifications, vous pouvez démarrer votre application dans un conteneur. Ensuite, continuez à apporter des modifications, en les regardant comme vous le feriez avec IIS Express.

1. Assurez-vous que Docker est configuré pour utiliser le type de conteneur (Linux ou Windows) que vous utilisez. Cliquez à droite sur l’icône Docker sur la barre des tâches, et choisissez **Switch to Linux containers** ou Switch to Windows **containers,** le cas échéant.

1. (.NET Core 3 et plus tard seulement) Modifier votre code et rafraîchir le site en cours d’exécution tel que décrit dans cette section n’est pas activé dans les modèles par défaut dans .NET Core >'3.0. Pour l’activer, ajoutez le package NuGet [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/). Dans *Startup.cs*, ajouter un appel à `IMvcBuilder.AddRazorRuntimeCompilation` la méthode `ConfigureServices` d’extension au code dans la méthode. Vous n’avez besoin que de ce activé en mode DEBUG, alors codez-le comme suit :

    ```csharp
    public IWebHostEnvironment Env { get; set; }
    
    public void ConfigureServices(IServiceCollection services)
    {
        IMvcBuilder builder = services.AddRazorPages();
    
    #if DEBUG
        if (Env.IsDevelopment())
        {
            builder.AddRazorRuntimeCompilation();
        }
    #endif
    
        // code omitted for brevity
    }
    ```

   Pour plus d’informations, voir [la compilation de fichiers Razor dans ASP.NET Core](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1).

1. Définir **la configuration de la solution** à **Debug**. Ensuite, appuyez sur **Ctrl**+**F5** pour construire votre image Docker et l’exécuter localement.

    Lorsque l’image du conteneur est construite et en cours d’exécution dans un conteneur Docker, Visual Studio lance l’application web dans votre navigateur par défaut.

1. Rendez-vous sur la page *Index.* Nous apporterons des modifications sur cette page.
1. Retour à Visual Studio et ouvert *Index.cshtml*.
1. Ajoutez le contenu HTML suivant à la fin du fichier, puis enregistrez les modifications.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. Dans la fenêtre de sortie, lorsque la version .NET est terminée et que vous voyez les lignes suivantes, retournez à votre navigateur et actualisez la page :

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Vos modifications ont été appliquées !

### <a name="debug-with-breakpoints"></a>Déboguer à l’aide de points d’arrêt

Souvent, les changements nécessitent une inspection plus approfondie. Vous pouvez utiliser les fonctionnalités de débogage de Visual Studio pour cette tâche.

1. Dans Visual Studio, ouvert *Index.cshtml.cs*.
2. Remplacer le contenu `OnGet` de la méthode par le code suivant :

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. À gauche de la ligne de code, définissez un point d’arrêt.
4. Pour commencer à débogage et frapper le point d’arrêt, appuyez sur F5.
5. Passez à Visual Studio pour afficher le point d’arrêt. Inspecter les valeurs.

   ![Point d’arrêt](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>Créer une application console .NET Framework

Lorsque vous utilisez des projets d’application de consoles framework .NET, la possibilité d’ajouter le support Docker sans orchestration n’est pas prise en charge. Vous pouvez toujours utiliser la procédure suivante, même si vous n’utilisez qu’un seul projet Docker.

1. Créez un nouveau projet d’application .NET Framework Console.
1. Dans Solution Explorer, cliquez à droite sur le nœud du projet, puis sélectionnez **Add** > **Container Orchestration Support**.  Dans la boîte de dialogue qui apparaît, sélectionnez **Docker Compose**. Un Dockerfile est ajouté à votre projet et un projet Docker Compose avec des fichiers de support associés est ajouté.

### <a name="debug-with-breakpoints"></a>Déboguer à l’aide de points d’arrêt

1. Dans Solution Explorer, ouvrir *Program.cs*.
2. Remplacer le contenu `Main` de la méthode par le code suivant :

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. Définissez un point d’arrêt à gauche de la ligne de code.
4. Appuyez sur F5 pour commencer à débogage et frapper le point d’arrêt.
5. Passez à Visual Studio pour afficher le point d’arrêt et inspecter les valeurs.

   ![Point d’arrêt](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Réutilisation des conteneurs

Pendant le cycle de développement, Visual Studio ne reconstruit que vos images de conteneurs et le conteneur lui-même lorsque vous changez le Dockerfile. Si vous ne modifiez pas le Dockerfile, Visual Studio réutilise le conteneur d’une course antérieure.

Si vous avez modifié manuellement votre conteneur et que vous souhaitez redémarrer avec une image de conteneur propre, utilisez la commande **Build** > **Clean** dans Visual Studio, puis construisez normalement.

## <a name="troubleshoot"></a>Dépanner

Apprenez à [dépanner Visual Studio Docker développement](troubleshooting-docker-errors.md).

## <a name="next-steps"></a>Étapes suivantes

Obtenez plus de détails en lisant [Comment Visual Studio construit des applications conteneurisées](container-build.md).

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>En savoir plus sur Docker avec Visual Studio, Windows et Azure

* En savoir plus sur [le développement de conteneurs avec Visual Studio](/visualstudio/containers).
* Pour construire et déployer un conteneur Docker, voir [l’intégration Docker pour Azure Pipelines](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker).
* Pour un index des articles Windows Server et Nano Server, voir [les informations sur les conteneurs Windows](/virtualization/windowscontainers/).
* En savoir plus sur [Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) et consulter la [documentation du service Azure Kubernetes](/azure/aks).
