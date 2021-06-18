---
title: Déboguer des applications dans un conteneur d’ancrage local | Microsoft Docs
description: Découvrez comment modifier une application en cours d’exécution dans un conteneur d’ancrage local, actualiser le conteneur par le biais de la modification et de l’actualisation, puis définir des points d’arrêt de débogage.
ms.author: ghogen
author: ghogen
manager: jmartens
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: how-to
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 8fb821acb48dd05aa09723fe5c6c254e7d1ca648
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306382"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Déboguer des applications dans un conteneur d’ancrage local

Visual Studio offre un moyen cohérent de développer des conteneurs d’ancrage et de valider votre application localement.
Vous pouvez exécuter et déboguer vos applications dans des conteneurs Linux ou Windows qui s’exécutent sur votre bureau Windows local avec Dockr, et vous n’êtes pas obligé de redémarrer le conteneur chaque fois que vous apportez une modification au code.

Cet article explique comment utiliser Visual Studio pour démarrer une application dans un conteneur d’ancrage local, apporter des modifications, puis actualiser le navigateur pour voir les modifications. Cet article vous montre également comment définir des points d’arrêt pour le débogage des applications en conteneur. Les types de projets pris en charge incluent .NET Framework et les applications Web et de console .NET Core. Dans cet article, nous utilisons ASP.NET Core applications Web et les applications de la console .NET Framework.

Si vous disposez déjà d’un projet d’un type pris en charge, Visual Studio peut créer un fichier dockerfile et configurer votre projet pour qu’il s’exécute dans un conteneur. Consultez [conteneurs Tools dans Visual Studio](overview.md).

## <a name="prerequisites"></a>Prérequis

Pour déboguer des applications dans un conteneur d’ancrage local, les outils suivants doivent être installés :

::: moniker range="vs-2017"

* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) avec la charge de travail de développement Web installée

::: moniker-end

::: moniker range="vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) avec la charge de travail de développement Web installée

::: moniker-end

::: moniker range="vs-2022"

* [Visual Studio 2022 Preview]() avec la charge de travail de développement Web installée

::: moniker-end

Pour exécuter des conteneurs de l’arrimeur localement, vous devez disposer d’un client Dockr local. Vous pouvez utiliser [docker pour Windows](https://www.docker.com/get-docker), qui utilise Hyper-V et requiert Windows 10.

Les conteneurs d’ancrage sont disponibles pour les projets .NET Framework et .NET Core. Examinons ces deux exemples. Tout d’abord, nous examinons une application Web .NET Core. Ensuite, nous examinons une application console .NET Framework.

## <a name="create-a-web-app"></a>Créer une application web

Si vous avez un projet et que vous avez ajouté la prise en charge de l’ancrage comme décrit dans la [vue d’ensemble](overview.md), ignorez cette section.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Modifier votre code et actualiser

Pour effectuer une itération rapide des modifications, vous pouvez démarrer votre application dans un conteneur. Ensuite, continuez à apporter des modifications, en les affichant comme vous le feriez avec IIS Express.

1. Assurez-vous que l’arrimeur est configuré pour utiliser le type de conteneur (Linux ou Windows) que vous utilisez. Cliquez avec le bouton droit sur l’icône de l’ancrage dans la barre des tâches, puis choisissez **basculer vers les conteneurs Linux** ou **basculez vers les conteneurs Windows** , le cas échéant.

1. (.NET Core 3 et versions ultérieures uniquement) La modification de votre code et l’actualisation du site en cours d’exécution, comme décrit dans cette section, ne sont pas activées dans les modèles par défaut de .NET Core >= 3,0. Pour l’activer, ajoutez le package NuGet [Microsoft. AspNetCore. Mvc. Razor. RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/). Dans *Startup. cs*, ajoutez un appel à la méthode `IMvcBuilder.AddRazorRuntimeCompilation` d’extension au code de la `ConfigureServices` méthode. Vous n’avez besoin que de cette option activée en mode débogage, donc codez-la comme suit :

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

    Modifiez la `Startup` méthode comme suit :

    ```csharp
    public Startup(IConfiguration configuration, IWebHostEnvironment webHostEnvironment)
    {
        Configuration = configuration;
        Env = webHostEnvironment;
    }
    ```

   Pour plus d’informations, consultez la rubrique [compilation de fichiers Razor dans ASP.net Core](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1&preserve-view=true).

1. Définissez **configuration** de la solution à **Déboguer**. Ensuite, appuyez sur **CTRL** + **F5** pour générer votre image d’ancrage et l’exécuter localement.

    Lorsque l’image de conteneur est générée et en cours d’exécution dans un conteneur d’ancrage, Visual Studio lance l’application Web dans votre navigateur par défaut.

1. Accédez à la page *index* . Nous allons apporter des modifications sur cette page.
1. Revenez à Visual Studio et ouvrez *index. cshtml*.
1. Ajoutez le contenu HTML suivant à la fin du fichier, puis enregistrez les modifications.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. Dans la fenêtre sortie, lorsque la génération .NET est terminée et que les lignes suivantes s’affichent, revenez à votre navigateur et actualisez la page :

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Vos modifications ont été appliquées !

### <a name="debug-with-breakpoints"></a>Déboguer à l’aide de points d’arrêt

Souvent, les modifications nécessitent une inspection supplémentaire. Vous pouvez utiliser les fonctionnalités de débogage de Visual Studio pour cette tâche.

1. Dans Visual Studio, ouvrez *index. cshtml. cs*.
2. Remplacez le contenu de la méthode `OnGet` par le code suivant :

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. À gauche de la ligne de code, définissez un point d’arrêt.
4. Pour démarrer le débogage et atteindre le point d’arrêt, appuyez sur F5.
5. Basculez vers Visual Studio pour afficher le point d’arrêt. Inspectez les valeurs.

   ![Capture d’écran montrant une partie du code pour index. cshtml. cs dans Visual Studio avec un point d’arrêt défini à gauche d’une ligne de code mise en surbrillance en jaune.](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app&quot;></a>Créer une application console .NET Framework

Lorsque vous utilisez .NET Framework projets d’application console, l’option permettant d’ajouter la prise en charge de l’ancrage sans orchestration n’est pas prise en charge. Vous pouvez toujours utiliser la procédure suivante, même si vous n’utilisez qu’un seul projet d’ancrage.

1. Créez un projet d’application console .NET Framework.
1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le nœud du projet, puis sélectionnez **Ajouter** la  >  **prise en charge de l’orchestration de conteneur**.  Dans la boîte de dialogue qui s’affiche, sélectionnez **docker compose**. Un fichier dockerfile est ajouté à votre projet et un projet de Docker Compose avec les fichiers de support associés est ajouté.

### <a name=&quot;debug-with-breakpoints&quot;></a>Déboguer à l’aide de points d’arrêt

1. Dans Explorateur de solutions, ouvrez *Program. cs*.
2. Remplacez le contenu de la méthode `Main` par le code suivant :

   ```csharp
       System.Console.WriteLine(&quot;Hello, world!");
   ```

3. Définissez un point d’arrêt à gauche de la ligne de code.
4. Appuyez sur F5 pour démarrer le débogage et atteindre le point d’arrêt.
5. Basculez vers Visual Studio pour afficher le point d’arrêt et inspecter les valeurs.

   ![Capture d’écran de la fenêtre de code pour Program. cs dans Visual Studio avec un point d’arrêt défini à gauche d’une ligne de code mise en surbrillance en jaune.](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Réutilisation de conteneur

Pendant le cycle de développement, Visual Studio reconstruit uniquement vos images conteneur et le conteneur lui-même lorsque vous modifiez le fichier dockerfile. Si vous ne modifiez pas le fichier dockerfile, Visual Studio réutilise le conteneur à partir d’une exécution antérieure.

Si vous avez modifié votre conteneur manuellement et souhaitez redémarrer avec une image de conteneur propre, utilisez la  >  commande de **nettoyage** de build dans Visual Studio, puis générez la valeur normal.

## <a name="troubleshoot"></a>Dépanner

Découvrez comment [résoudre les problèmes de développement de l’ancrage de Visual Studio](troubleshooting-docker-errors.md).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [comment Visual Studio génère des applications en conteneur](container-build.md).

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>En savoir plus sur Docker avec Visual Studio, Windows et Azure

* En savoir plus sur le [développement de conteneurs avec Visual Studio](./index.yml).
* Pour générer et déployer un conteneur d’ancrage, consultez [intégration de l’amarrage pour Azure pipelines](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker).
* Pour obtenir un index des articles Windows Server et nano Server, consultez les [informations relatives au conteneur Windows](/virtualization/windowscontainers/).
* Découvrez [Azure Kubernetes service](https://azure.microsoft.com/services/kubernetes-service/) et consultez la [documentation du service Azure Kubernetes](/azure/aks).
