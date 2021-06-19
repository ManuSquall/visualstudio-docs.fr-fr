---
title: 'Didacticiel : ouvrir un projet à partir d’un référentiel dans Visual Studio 2019'
description: Découvrez comment ouvrir un projet dans un référentiel git ou Azure DevOps à l’aide de Visual Studio 2019.
ms.custom: vs-acquisition, get-started
ms.date: 03/18/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
monikerRange: vs-2019
ms.openlocfilehash: b6f7cd57a1753ca5926ac73a9bb4c8c918d1bd10
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389941"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Didacticiel : ouvrir un projet à partir d’un référentiel

Dans ce didacticiel, vous allez utiliser Visual Studio pour vous connecter à un référentiel pour la première fois puis ouvrir un projet à partir de celui-ci.

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

## <a name="open-a-project-from-a-github-repo"></a>Ouvrir un projet à partir d’un référentiel GitHub

La façon dont vous ouvrez un projet à partir d’un référentiel GitHub à l’aide de Visual Studio 2019 dépend de la version dont vous disposez. Plus précisément, si vous avez installé la version [**16,8**](/visualstudio/releases/2019/release-notes/) ou une version ultérieure, vous disposez d’une nouvelle [expérience git entièrement intégrée dans Visual Studio](../ide/git-with-visual-studio.md) .

Mais quelle que soit la version que vous avez installée, vous pouvez toujours ouvrir un projet à partir d’un GitHub référentiel avec Visual Studio.

#### <a name="168-and-later"></a>[16,8 et versions ultérieures](#tab/vs168later)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Cloner un référentiel GitHub, puis ouvrir un projet

1. Ouvrez Visual Studio 2019.

1. Dans la fenêtre Démarrer, sélectionnez **cloner un référentiel**.

   ![Capture d’écran de la boîte de dialogue cloner un référentiel dans Visual Studio 2019 version 16,8 et versions ultérieures](../ide/media/vs-2019/clone-repository.png)

1. Entrez ou tapez l’emplacement du référentiel, puis sélectionnez **cloner**.

   ![Capture d’écran de la boîte de dialogue cloner un référentiel dans laquelle vous entrez une URL référentiel git dans Visual Studio 2019 version 16,8 et versions ultérieures](../ide/media/vs-2019/clone-repository-enter-location.png)

1. Vous pouvez être invité à entrer vos informations de connexion utilisateur dans la boîte de dialogue **informations d’utilisateur git** . Vous pouvez ajouter vos informations ou modifier les informations par défaut qu’elles fournissent.

   ![Capture d’écran de la boîte de dialogue informations utilisateur git dans laquelle vous entrez ou modifiez les informations de votre compte dans Visual Studio 2019 version 16,8 et versions ultérieures](../ide/media/vs-2019/git-user-information-dialog.png)

    Sélectionnez **Enregistrer** pour ajouter les informations à votre fichier global. gitconfig. (Ou vous pouvez choisir de le faire plus tard en sélectionnant **Annuler**.)

    > [!TIP]
    > Pour plus d’informations sur la connexion à Visual Studio, consultez la page [se connecter à Visual Studio](../ide/signing-in-to-visual-studio.md) . Et pour obtenir des informations spécifiques sur l’utilisation de votre compte GitHub pour vous connecter, consultez la page [utiliser les comptes GitHub dans Visual Studio](../ide/work-with-github-accounts.md) .

    Ensuite, Visual Studio charge et ouvre automatiquement la solution à partir du référentiel.

   ![Capture d’écran d’un projet dans Git qui est ouvert dans Explorateur de solutions dans Visual Studio 2019 version 16,8 et versions ultérieures](../ide/media/vs-2019/git-solution-explorer.png )

1. Si votre référentiel contient plusieurs solutions, vous les verrez dans Explorateur de solutions. Vous pouvez afficher la liste des solutions en sélectionnant le bouton **basculer les vues** dans Explorateur de solutions.

   ![Capture d’écran d’un projet dans Git qui est ouvert dans Explorateur de solutions, avec le bouton basculer les vues mis en surbrillance dans Visual Studio 2019 version 16,8 et versions ultérieures](../ide/media/vs-2019/git-solution-explorer-switch-views.png)

   Explorateur de solutions vous donne ensuite la possibilité d’ouvrir le dossier racine dans l' **affichage des dossiers** ou de sélectionner un fichier solution à ouvrir.

   ![Capture d’écran du fichier. sln dans Git qui est ouvert dans Explorateur de solutions, après avoir sélectionné le bouton basculer les vues dans Visual Studio 2019 version 16,8 et versions ultérieures](../ide/media/vs-2019/git-solution-explorer-view-solution.png)

    Pour basculer la vue, cliquez à nouveau sur le bouton **basculer les vues** .

    > [!TIP]
    > Vous pouvez également utiliser le menu **git** dans l’IDE de Visual Studio pour cloner un référentiel et ouvrir un projet.
    >
    > ![Capture d’écran du menu git dans Visual Studio 2019 version 16,8 et versions ultérieures](../ide/media/vs-2019/git-menu-clone-create-git-repository.png)

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>Ouvrir un projet localement à partir d’un référentiel GitHub précédemment cloné

1. Ouvrez Visual Studio 2019.

1. Dans la fenêtre Démarrer, sélectionnez **ouvrir un projet ou une solution**.

    Visual Studio ouvre une instance de l’Explorateur de fichiers, où vous pouvez accéder à votre solution ou à votre projet, puis le sélectionner pour l’ouvrir.

   ![Capture d’écran de la fenêtre ouvrir un projet ou une solution dans Visual Studio 2019, version 16,8 et ultérieure](../ide/media/vs-2019/open-local-project-from-cloned-repo.png)

    Si vous avez récemment ouvert le projet ou la solution, sélectionnez-le dans la section **ouvrir récent** pour le rouvrir rapidement.

    > [!TIP]
    > Vous pouvez également utiliser le menu **git** dans l’IDE de Visual Studio pour ouvrir des dossiers et des fichiers locaux à partir d’un référentiel que vous avez précédemment cloné.
    >
    > ![Capture d’écran du menu git dans Visual Studio 2019, version 16,8 et ultérieure, avec l’option dépôts locaux développée](../ide/media/vs-2019/git-menu-local-repositories.png)

    Commencez à coder !

#### <a name="167-and-earlier"></a>[16,7 et versions antérieures](#tab/vs167earlier)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Cloner un référentiel GitHub, puis ouvrir un projet

1. Ouvrez Visual Studio 2019.

1. Dans la fenêtre Démarrer, sélectionnez **cloner ou extraire du code**.

   ![Capture d’écran de la fenêtre créer un nouveau projet dans Visual Studio 2019 version 16,7 et antérieure](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Entrez ou tapez l’emplacement du référentiel, puis sélectionnez **cloner**.

   ![Capture d’écran de la fenêtre « cloner ou extraire le code » dans Visual Studio 2019 version 16,7 et antérieure](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio ouvre le projet à partir du dépôt.

1. Si un fichier solution est disponible, il apparaît dans le menu contextuel « Solutions et dossiers ». Sélectionnez-la et Visual Studio ouvre votre solution.

   ![Capture d’écran de la liste déroulante Explorateur de solutions dans Visual Studio 2019 version 16,7 et versions antérieures](./media/open-proj-repo-github-solutions-folders-picker.png)

   Si vous n’avez pas de fichier solution (en particulier un fichier. sln) dans votre référentiel, le menu volant indique « aucune solution n’a été trouvée ». Vous pouvez toutefois double-cliquer sur n’importe quel fichier dans le menu de dossier pour l’ouvrir dans l’éditeur de code Visual Studio.

    Commencez à coder !

---

> [!NOTE]
> Pour obtenir des informations spécifiques à Visual Studio 2017, consultez la page [ouvrir un projet à partir d’un référentiel dans Visual studio 2017](tutorial-open-project-from-repo-visual-studio-2017.md) .

## <a name="connect-to-an-azure-devops-server"></a>Se connecter à un serveur Azure DevOps

Ce que vous voyez quand vous vous connectez à un serveur Azure DevOps à l’aide de Visual Studio 2019 dépend de la version dont vous disposez. Plus précisément, si vous avez installé la version [**16,8**](/visualstudio/releases/2019/release-notes/) ou une version ultérieure, nous avons modifié l’interface utilisateur pour prendre en charge une nouvelle [expérience git entièrement intégrée dans Visual](../ide/git-with-visual-studio.md) Studio dans Visual Studio.

Mais quelle que soit la version que vous avez installée, vous pouvez toujours vous connecter à un serveur Azure DevOps à l’aide de Visual Studio.

#### <a name="168-and-later"></a>[16,8 et versions ultérieures](#tab/vs168later)

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

#### <a name="167-and-earlier"></a>[16,7 et versions antérieures](#tab/vs167earlier)

1. Ouvrez Visual Studio 2019.

1. Dans la fenêtre Démarrer, sélectionnez **cloner ou extraire du code**.

   ![Capture d’écran de la fenêtre créer un nouveau projet dans Visual Studio 2019 version 16,7 et antérieure](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Dans la section **Parcourir un référentiel** , sélectionnez **Azure DevOps**.

   ![Capture d’écran de la fenêtre « cloner ou extraire le code » avec la section « parcourir un référentiel » qui répertorie Azure DevOps dans Visual Studio 2019 version 16,7 et versions antérieures](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Si une fenêtre de connexion s’affiche, connectez-vous à votre compte.

1. Dans la boîte de dialogue **se connecter à un projet** , choisissez le référentiel auquel vous souhaitez vous connecter, puis sélectionnez **cloner**.

      ![Capture d’écran de la boîte de dialogue « se connecter à un projet » générée à partir de Visual Studio 2019 version 16,7 et antérieure](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Ce que vous voyez dans la zone de liste varie selon les référentiels Azure DevOps auxquels vous avez accès.

   Visual Studio ouvre **Team Explorer** et une notification s’affiche quand le clone est complet.

     ![Capture d’écran de la fenêtre de Team Explorer dans Visual Studio 2019 version 16,7 et antérieure, une fois le clone terminé](./media/vs-2019/clone-complete-azure-devops.png)

1. Pour afficher vos dossiers et fichiers, sélectionnez le lien Afficher l' **affichage des dossiers** .

     ![Capture d’écran de la section solutions de la fenêtre Team Explorer dans Visual Studio 2019 version 16,7 et antérieure, une fois le clone terminé](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio ouvre l’**Explorateur de solutions**.

1. Choisissez le lien **solutions et dossiers** pour rechercher un fichier solution (plus précisément un fichier. sln) à ouvrir.

      ![Capture d’écran de la notification « solutions et dossiers » de Team Explorer dans Visual Studio 2019 version 16,7 et versions antérieures](./media/open-proj-repo-solutions-folders.png)

   Si vous n’avez pas de fichier solution dans votre référentiel, le message « aucune solution trouvée » s’affiche. Vous pouvez toutefois double-cliquer sur n’importe quel fichier dans le menu de dossier pour l’ouvrir dans l’éditeur de code Visual Studio.

---

## <a name="next-steps"></a>Étapes suivantes

Si vous êtes prêt à coder avec Visual Studio, suivez un des didacticiels spécifiques au langage suivants :

- [Didacticiels Visual Studio | **C#**](./csharp/index.yml)
- [Didacticiels Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Didacticiels Visual Studio | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Didacticiels Visual Studio | **Python**](../python/index.yml)
- [Didacticiels Visual Studio | **JavaScript**, **TypeScript** et **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Voir aussi

- [Ouvrir un projet à partir d’un référentiel dans Visual Studio 2017](tutorial-open-project-from-repo-visual-studio-2017.md)
- [Nouvelle expérience git dans Visual Studio 2019](../ide/git-with-visual-studio.md)
- [Comparer git et Team Explorer côte à côte](../ide/git-team-explorer-feature-comparison.md)
- [Azure DevOps Services : prise en main de Azure Repos et de Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn : prise en main d’Azure DevOps](/learn/modules/get-started-with-devops/)
