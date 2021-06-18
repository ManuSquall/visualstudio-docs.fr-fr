---
title: Se connecter aux projets dans Team Explorer
description: Découvrez comment utiliser Team Explorer dans Visual Studio pour travailler avec les membres de l’équipe pour développer et gérer des projets.
ms.custom: SEO-VS-2020
ms.date: 06/11/2021
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
monikerRange: <=vs-2019
ms.openlocfilehash: b45399f7a4115ce5946a67caca22ca92148e7434
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308244"
---
# <a name="connect-to-projects-in-team-explorer"></a>Se connecter aux projets dans Team Explorer

::: moniker range="vs-2017"

Utilisez la fenêtre d’outil **Team Explorer** pour coordonner vos efforts de codage avec d’autres membres d’équipe afin de développer un projet, et pour gérer le travail assigné à vous-même, à votre équipe ou à vos projets. **Team Explorer** connecte Visual Studio aux dépôts Git et GitHub, aux référentiels Team Foundation Version Control (TFVC) et aux projets hébergés sur [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) ou un serveur [Azure DevOps Server](/azure/devops/index-all) sur site (anciennement appelé TFS). Vous pouvez gérer le code source, les éléments de travail et les générations.

::: moniker-end

::: moniker range="vs-2019"

Team Explorer connecte Visual Studio aux référentiels de contrôle de version Team Foundation (TFVC) et aux projets hébergés sur [Azure DevOps services](/azure/devops/user-guide/what-is-azure-devops-services) ou sur un [Azure DevOps Server](/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops&preserve-view=true) local (anciennement appelé TFS). Vous pouvez gérer le code source, les éléments de travail et les générations.

> [!IMPORTANT]
> Avec la publication de Visual Studio 2019 [**version 16,8**](/visualstudio/releases/2019/release-notes-history), l’expérience de contrôle de version git est activée par défaut. Si vous souhaitez en savoir plus sur la façon dont elle est comparée à Team Explorer, consultez la [**comparaison côte à côte des pages git et Team Explorer**](../version-control/git-team-explorer-feature-comparison.md) .
>
> Toutefois, si vous préférez continuer à utiliser Team Explorer, accédez à **Outils** > **options** > **environnement** > **Aperçu fonctionnalités** , puis activez la case à cocher **nouvelle expérience utilisateur git** .

La façon dont vous utilisez Team Explorer pour vous connecter à un projet dépend de la version de Visual Studio 2019 que vous utilisez.

## <a name="in-version-168-and-later"></a>Dans la version 16,8 et versions ultérieures

1. Ouvrez Visual Studio 2019.

1. Dans la fenêtre Démarrer, sélectionnez **cloner un référentiel**.

   ![Capture d’écran de la boîte de dialogue cloner un référentiel dans Visual Studio 2019 version 16,8 et versions ultérieures, pour Azure DevOps](../ide/media/vs-2019/clone-repository.png)

1. Dans la section **Parcourir un référentiel** , sélectionnez **Azure DevOps**.

    ![Capture d’écran de la section « parcourir un référentiel » de la boîte de dialogue « se connecter à un projet » dans Visual Studio 2019 version 16,8 et versions ultérieures](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Si une fenêtre de connexion s’affiche, connectez-vous à votre compte.

1. Dans la boîte de dialogue **se connecter à un projet** , choisissez le référentiel auquel vous souhaitez vous connecter, puis sélectionnez **cloner**.

      ![Capture d’écran de la boîte de dialogue « se connecter à un projet » générée à partir de Visual Studio 2019 version 16,8 et versions ultérieures](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > Si vous ne voyez pas une liste préremplie de pensions à laquelle se connecter, sélectionnez **ajouter Azure DevOps Server** pour entrer une URL de serveur. (Vous pouvez également voir un message « aucun serveur trouvé » incluant des liens pour ajouter un Azure DevOps Server existant ou pour créer un compte Azure DevOps.)

   Ensuite, Visual Studio ouvre **Explorateur de solutions** qui affiche les dossiers et les fichiers.

1. Sélectionnez l’onglet **Team Explorer** pour afficher les actions Azure DevOps.

      ![Capture d’écran de la boîte de dialogue « Team Explorer » générée à partir de Visual Studio 2019 version 16,8 et versions ultérieures](../ide/media/vs-2019/team-explorer-azure-devops.png)

## <a name="in-version-167-and-earlier"></a>Dans la version 16,7 et les versions antérieures

1. Ouvrez Visual Studio 2019.

1. Dans la fenêtre Démarrer, sélectionnez **cloner ou extraire du code**.

   ![Capture d’écran de la fenêtre créer un nouveau projet dans Visual Studio 2019 version 16,7 et antérieure](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Dans la section **Parcourir un référentiel** , sélectionnez **Azure DevOps**.

   ![Capture d’écran de la fenêtre « cloner ou extraire le code » avec la section « parcourir un référentiel » qui répertorie Azure DevOps dans Visual Studio 2019 version 16,7 et versions antérieures](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Si une fenêtre de connexion s’affiche, connectez-vous à votre compte.

1. Dans la boîte de dialogue **se connecter à un projet** , choisissez le référentiel auquel vous souhaitez vous connecter, puis sélectionnez **cloner**.

      ![Capture d’écran de la boîte de dialogue « se connecter à un projet » générée à partir de Visual Studio 2019 version 16,7 et antérieure](../get-started/media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Ce que vous voyez dans la zone de liste varie selon les référentiels Azure DevOps auxquels vous avez accès.

   Visual Studio ouvre **Team Explorer** et une notification s’affiche quand le clone est complet.

     ![Capture d’écran de la fenêtre de Team Explorer dans Visual Studio 2019 version 16,7 et antérieure, une fois le clone terminé](../get-started/media/vs-2019/clone-complete-azure-devops.png)

1. Pour afficher vos dossiers et fichiers, sélectionnez le lien Afficher l' **affichage des dossiers** .

     ![Capture d’écran de la section solutions de la fenêtre Team Explorer dans Visual Studio 2019 version 16,7 et antérieure, une fois le clone terminé](../get-started/media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio ouvre l’**Explorateur de solutions**.

1. Choisissez le lien **solutions et dossiers** pour rechercher un fichier solution (plus précisément un fichier. sln) à ouvrir.

      ![Capture d’écran de la notification « solutions et dossiers » de Team Explorer dans Visual Studio 2019 version 16,7 et versions antérieures](../get-started/media/open-proj-repo-solutions-folders.png)

   Si vous n’avez pas de fichier solution dans votre référentiel, le message « aucune solution trouvée » s’affiche. Vous pouvez toutefois double-cliquer sur n’importe quel fichier dans le menu de dossier pour l’ouvrir dans l’éditeur de code Visual Studio.

::: moniker-end

::: moniker range="vs-2017&quot;

![Page d’accueil de Team Explorer dans Visual Studio](media/team-explorer/team-explorer.png &quot;La page Team Explorer-page d’hébergement de Visual Studio.")

> [!TIP]
> Si vous ouvrez Visual Studio et que **Team Explorer** ne s’affiche pas, ouvrez-le en choisissant **Afficher**  >  les **Team Explorer** dans la barre de menus, ou en appuyant sur **CTRL** + **&#92;**, **CTRL** + **M**.

## <a name="connect-to-a-project-or-repository"></a>Se connecter à un projet ou à un référentiel

Connectez-vous à un projet ou à un référentiel sur la page **Se connecter**.

![Page Se connecter dans Team Explorer](media/team-explorer/connect.png "Page Team Explorer-Connect dans Visual Studio")

Pour se connecter à un projet :

1. Ouvrez la page **Se connecter** en choisissant l’icône **Gérer les connexions**.

   ![Bouton Gérer les connexions dans Team Explorer](media/team-explorer/manage-connections.png "Le bouton Team Explorer-gérer les connexions dans Visual Studio.")

1. Sur la page de **connexion** , choisissez **gérer connexions** > **connexion à un projet**.

   ![Se connecter à un projet dans Team Explorer](media/team-explorer/connect-project.png "L’option Team Explorer-se connecter à un projet dans Visual Studio.")

> [!TIP]
> Si vous souhaitez ouvrir un projet à partir d’un référentiel, consultez [ouvrir un projet à partir d’un référentiel](../get-started/tutorial-open-project-from-repo-visual-studio-2017.md). Si vous souhaitez créer un projet ou ajouter des utilisateurs à un projet, consultez [créer un projet (Azure DevOps)](/azure/devops/organizations/projects/create-project) et [Ajouter des utilisateurs à un projet ou une équipe (Azure DevOps)](/azure/devops/organizations/security/add-users-team-project).

::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Comparer git et Team Explorer côte à côte](git-team-explorer-feature-comparison.md)
- [Nouvelle expérience git dans Visual Studio](git-with-visual-studio.md)
- [Informations de référence sur Team Explorer](reference/team-explorer-reference.md)
- [Se connecter à un projet (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [Résoudre les problèmes de connexion à un projet](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
