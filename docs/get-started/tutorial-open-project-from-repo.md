---
title: 'Didacticiel : ouvrir un projet à partir d’un référentiel'
description: Découvrez comment ouvrir un projet dans un référentiel Git ou Azure DevOps à l’aide de Visual Studio.
ms.custom: get-started
ms.date: 03/30/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3af54d663cee1ad2b2dd4e8241678b88c635d376
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "70180443"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Didacticiel : ouvrir un projet à partir d’un référentiel

Dans ce didacticiel, vous allez utiliser Visual Studio pour vous connecter à un référentiel pour la première fois puis ouvrir un projet à partir de celui-ci.

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>Ouvrir un projet à partir d’un référentiel GitHub

::: moniker range="vs-2017"

1. Ouvrez Visual Studio 2017.

1. Dans la barre de menus supérieure, choisissez **Fichier** > **Ouvrir** > **Ouvrir depuis le contrôle de code source**.

   Le volet **Team Explorer - Se connecter** s’affiche.

    ![La fenêtre Team Explorer dans l’IDE de Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Dans la section **Référentiels Git locaux**, choisissez **Cloner**.

    ![Choisir Cloner dans la section Référentiels Git locaux](./media/open-proj-repo-local-git-repo-clone.png)

1. Dans la zone intitulée ***Entrez l’URL d’un référentiel Git à cloner***, tapez ou collez l’URL de votre référentiel, puis appuyez sur **Entrée**. (Vous pouvez recevoir une invite de connexion GitHub. Si c’est le cas, faites-le.)

   Lorsque Visual Studio a cloné votre référentiel, Team Explorer est fermé et l’Explorateur de solutions s’affiche. Le message *Cliquez sur "Solutions et dossiers" ci-dessus pour afficher une liste de solutions* s’affiche. Choisissez **Solutions et dossiers**.

   ![Choisir « Solutions et dossiers » dans l’Explorateur de solutions](./media/open-proj-repo-github-solutions-folders.png)

1. Si un fichier solution est disponible, il apparaît dans le menu contextuel « Solutions et dossiers ». Choisissez-le, Visual Studio ouvre alors votre solution.

   ![Choisir ce que vous souhaitez ouvrir dans la liste déroulante de l’Explorateur de solutions](./media/open-proj-repo-github-solutions-folders-picker.png)

   Si vous n’avez pas de fichier solution (plus précisément, un fichier .sln) dans votre référentiel, le menu contextuel indique « Solutions introuvables ». Vous pouvez toutefois double-cliquer sur n’importe quel fichier dans le menu de dossier pour l’ouvrir dans l’éditeur de code Visual Studio.

### <a name="review-your-work"></a>Passer en revue votre travail

Regardez l’animation suivante pour vérifier le travail que vous avez effectué dans la section précédente.

   ![Animation d’ouverture d’un projet dans un référentiel GitHub à l’aide de Visual Studio](./media/open-project-from-github.gif)

::: moniker-end

::: moniker range="vs-2019"

1. Ouvrez Visual Studio 2019.

1. Dans la fenêtre de démarrage, choisissez **Cloner ou extraire du code**.

   ![Afficher la fenêtre « Créer un projet »](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Entrez ou tapez l’emplacement du dépôt, puis choisissez **Cloner**.

   ![Afficher la fenêtre Cloner ou extraire du code](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio ouvre le projet à partir du dépôt.

1. Si un fichier solution est disponible, il apparaît dans le menu contextuel « Solutions et dossiers ». Choisissez-le, Visual Studio ouvre alors votre solution.

   ![Choisir ce que vous souhaitez ouvrir dans la liste déroulante de l’Explorateur de solutions](./media/open-proj-repo-github-solutions-folders-picker.png)

   Si vous n’avez pas de fichier solution (plus précisément, un fichier .sln) dans votre référentiel, le menu contextuel indique « Solutions introuvables ». Vous pouvez toutefois double-cliquer sur n’importe quel fichier dans le menu de dossier pour l’ouvrir dans l’éditeur de code Visual Studio.

::: moniker-end

## <a name="open-a-project-from-an-azure-devops-repo"></a>Ouvrir un projet à partir d’un référentiel Azure DevOps

::: moniker range="vs-2017"

1. Ouvrez Visual Studio 2017.

1. Dans la barre de menus supérieure, choisissez **Fichier** > **Ouvrir** > **Ouvrir depuis le contrôle de code source**.

   Le volet **Team Explorer - Se connecter** s’affiche.

    ![La fenêtre Team Explorer dans l’IDE de Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Voici deux façons de se connecter à votre référentiel Azure DevOps :

      - Dans la section **Fournisseurs de services hébergés**, choisissez **Se connecter...**.

        ![La section Fournisseurs de services hébergés de la fenêtre Team Explorer dans l’IDE de Visual Studio](./media/open-proj-repo-azure-devops.png)

      - Dans la liste déroulante **Gérer les connexions**, choisissez **Se connecter à un projet...**.

        ![La section Gérer les connexions de la fenêtre Team Explorer dans l’IDE de Visual Studio](./media/open-proj-repo-azuredevops-manage-connections.png)

1. Dans la boîte de dialogue **Se connecter à un projet**, sélectionnez le référentiel auquel vous souhaitez vous connecter, puis choisissez **Cloner**.

      ![La boîte de dialogue « Se connecter à un projet » qui est générée à partir de Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Ce que vous voyez dans la zone de liste varie selon les référentiels Azure DevOps auxquels vous avez accès.

1. Lorsque Visual Studio a cloné votre référentiel, Team Explorer est fermé et l’Explorateur de solutions s’affiche. Le message *Cliquez sur "Solutions et dossiers" ci-dessus pour afficher une liste de solutions* s’affiche. Choisissez **Solutions et dossiers**.

      ![La notification « Solutions et les dossiers » de Team Explorer dans Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Un fichier solution (plus précisément, un fichier .sln) apparaît dans le menu contextuel « Solutions et dossiers ». Choisissez-le, Visual Studio ouvre alors votre solution.

   Si vous n’avez pas de fichier solution dans votre référentiel, le menu contextuel indique « Solutions introuvables ». Vous pouvez toutefois double-cliquer sur n’importe quel fichier dans le menu de dossier pour l’ouvrir dans l’éditeur de code Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

1. Ouvrez Visual Studio 2019.

1. Dans la fenêtre de démarrage, choisissez **Cloner ou extraire du code**.

   ![Afficher la fenêtre « Créer un projet »](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Dans la section **Parcourir un dépôt**, choisissez **Azure DevOps**.

   ![Afficher la fenêtre Cloner ou extraire du code](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Si une fenêtre de connexion s’affiche, connectez-vous à votre compte.

1. Dans la boîte de dialogue **Se connecter à un projet**, sélectionnez le référentiel auquel vous souhaitez vous connecter, puis choisissez **Cloner**.

      ![La boîte de dialogue « Se connecter à un projet » qui est générée à partir de Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Ce que vous voyez dans la zone de liste varie selon les référentiels Azure DevOps auxquels vous avez accès.

   Visual Studio ouvre **Team Explorer** et une notification s’affiche quand le clone est complet.

     ![Fenêtre Team Explorer dans Visual Studio une fois que le clone est complet](./media/vs-2019/clone-complete-azure-devops.png)

1. Pour voir vos dossiers et fichiers, choisissez le lien **Présenter l’affichage des dossiers**.

     ![Section Solutions de la fenêtre Team Explorer dans Visual Studio une fois que le clone est complet](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio ouvre l’**Explorateur de solutions**.

1. Choisissez le lien **Solutions et dossiers** pour rechercher un fichier de solution (plus précisément, un fichier .sln) à ouvrir.

      ![La notification « Solutions et les dossiers » de Team Explorer dans Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Si vous n’avez pas de fichier de solution dans votre dépôt, un message « Solutions introuvables » s’affiche. Vous pouvez toutefois double-cliquer sur n’importe quel fichier dans le menu de dossier pour l’ouvrir dans l’éditeur de code Visual Studio.

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

Si vous êtes prêt à coder avec Visual Studio, suivez un des didacticiels spécifiques au langage suivants :

- [Didacticiels Visual Studio | **C#**](./csharp/index.yml)
- [Didacticiels Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Didacticiels Visual Studio | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Didacticiels Visual Studio | **Python**](/visualstudio/python/)
- [Didacticiels Visual Studio | **JavaScript**, **TypeScript** et **Node.js**](/visualstudio/javascript/)

## <a name="see-also"></a>Voir aussi

- [Azure DevOps Services : prise en main de Azure Repos et de Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn : prise en main d’Azure DevOps](/learn/modules/get-started-with-devops/)