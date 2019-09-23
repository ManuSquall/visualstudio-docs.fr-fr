---
title: Déboguer des applications dans un conteneur d’ancrage local | Microsoft Docs
description: Découvrez comment modifier une application en cours d’exécution dans un conteneur d’ancrage local, actualiser le conteneur par le biais de la modification et de l’actualisation, puis définir des points d’arrêt de débogage.
ms.author: ghogen
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: conceptual
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 5af092bbcb987f45b10121f37d40eaa5466c3da5
ms.sourcegitcommit: 2db01751deeee7b2bdb1db25419ea6706e6fcdf8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71062176"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Déboguer des applications dans un conteneur d’ancrage local

Visual Studio offre un moyen cohérent de développer dans un conteneur d’ancrage et de valider votre application localement. Vous n’êtes pas obligé de redémarrer le conteneur chaque fois que vous apportez une modification au code.

Cet article explique comment utiliser Visual Studio pour démarrer un ASP.NET Core application Web dans un conteneur d’ancrage local, apporter des modifications, puis actualiser le navigateur pour voir les modifications. Cet article vous montre également comment définir des points d’arrêt pour le débogage pour les applications Web ASP.NET Core en conteneur et les applications de console de .NET Framework.

## <a name="prerequisites"></a>Prérequis

Pour déboguer des applications dans un conteneur d’ancrage local, les outils suivants doivent être installés :

::: moniker range="vs-2017"

* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) avec la charge de travail de développement Web installée

::: moniker-end

::: moniker range="vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) avec la charge de travail de développement Web installée

::: moniker-end

Pour exécuter des conteneurs de l’arrimeur localement, vous devez disposer d’un client Dockr local. Vous pouvez utiliser la [boîte à outils](https://www.docker.com/products/docker-toolbox)de l’ancrage, qui nécessite la désactivation d’Hyper-V. Vous pouvez également utiliser [docker pour Windows](https://www.docker.com/get-docker), qui utilise Hyper-V et requiert Windows 10. 

Les conteneurs d’ancrage sont disponibles pour les projets .NET Framework et .NET Core. Examinons ces deux exemples. Tout d’abord, nous examinons une application Web .NET Core. Ensuite, nous examinons une application console .NET Framework.

## <a name="create-a-web-app"></a>Créer une application web

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Modifier votre code et actualiser

Pour effectuer une itération rapide des modifications, vous pouvez démarrer votre application dans un conteneur. Ensuite, continuez à apporter des modifications, en les affichant comme vous le feriez avec IIS Express.

1. Définissez **configuration** de la solution à **Déboguer**. Ensuite, appuyez sur **CTRL**+**F5** pour générer votre image d’ancrage et l’exécuter localement.

    Lorsque l’image de conteneur est générée et en cours d’exécution dans un conteneur d’ancrage, Visual Studio lance l’application Web dans votre navigateur par défaut.

2. Accédez à la page *index* . Nous allons apporter des modifications sur cette page.
3. Revenez à Visual Studio et ouvrez *index. cshtml*.
4. Ajoutez le contenu HTML suivant à la fin du fichier, puis enregistrez les modifications.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

5. Dans la fenêtre sortie, lorsque la génération .NET est terminée et que les lignes suivantes s’affichent, revenez à votre navigateur et actualisez la page :

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Vos modifications ont été appliquées.

### <a name="debug-with-breakpoints"></a>Déboguer avec des points d’arrêt

Souvent, les modifications nécessitent une inspection supplémentaire. Vous pouvez utiliser les fonctionnalités de débogage de Visual Studio pour cette tâche.

1. Dans Visual Studio, ouvrez *index.cshtml.cs*.
2. Remplacez le contenu de la `OnGet` méthode par le code suivant :

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. À gauche de la ligne de code, définissez un point d’arrêt.
4. Pour démarrer le débogage et atteindre le point d’arrêt, appuyez sur F5.
5. Basculez vers Visual Studio pour afficher le point d’arrêt. Inspectez les valeurs.

   ![Point d'arrêt](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>Créer une application console .NET Framework

Lorsque vous utilisez .NET Framework projets d’application console, l’option permettant d’ajouter la prise en charge de l’ancrage sans orchestration n’est pas prise en charge. Vous pouvez toujours utiliser la procédure suivante, même si vous n’utilisez qu’un seul projet d’ancrage.

1. Créez un projet d’application console .NET Framework.
1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le nœud du projet, puis sélectionnez **Ajouter** > la**prise en charge de l’orchestration de conteneur**.  Dans la boîte de dialogue qui s’affiche, sélectionnez **docker compose**. Un fichier dockerfile est ajouté à votre projet et un projet de Docker Compose avec les fichiers de support associés est ajouté.

### <a name="debug-with-breakpoints"></a>Déboguer avec des points d’arrêt

1. Dans Explorateur de solutions, ouvrez *Program.cs*.
2. Remplacez le contenu de la `Main` méthode par le code suivant :

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. Définissez un point d’arrêt à gauche de la ligne de code.
4. Appuyez sur F5 pour démarrer le débogage et atteindre le point d’arrêt.
5. Basculez vers Visual Studio pour afficher le point d’arrêt et inspecter les valeurs.

   ![Point d'arrêt](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Réutilisation de conteneur

Pendant le cycle de développement, Visual Studio reconstruit uniquement vos images conteneur et le conteneur lui-même lorsque vous modifiez le fichier dockerfile. Si vous ne modifiez pas le fichier dockerfile, Visual Studio réutilise le conteneur à partir d’une exécution antérieure.

Si vous avez modifié votre conteneur manuellement et souhaitez redémarrer avec une image de conteneur propre, utilisez la commande de**nettoyage** de **Build** > dans Visual Studio, puis générez la valeur normal.

## <a name="troubleshoot"></a>Résolution des problèmes

Découvrez comment [résoudre les problèmes de développement de l’ancrage de Visual Studio](troubleshooting-docker-errors.md).

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>En savoir plus sur la station d’accueil avec Visual Studio, Windows et Azure

* En savoir plus sur le [développement de conteneurs avec Visual Studio](/visualstudio/containers).
* Pour générer et déployer un conteneur d’ancrage, consultez [intégration de l’amarrage pour Azure pipelines](https://aka.ms/dockertoolsforvsts).
* Pour obtenir un index des articles Windows Server et nano Server, consultez les [informations relatives au conteneur Windows](https://aka.ms/containers).
* Découvrez [Azure Kubernetes service](https://azure.microsoft.com/services/kubernetes-service/) et consultez la [documentation du service Azure Kubernetes](/azure/aks).
