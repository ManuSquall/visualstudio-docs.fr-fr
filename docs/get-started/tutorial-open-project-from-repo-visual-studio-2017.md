---
title: 'Didacticiel : ouvrir un projet à partir d’un référentiel dans Visual Studio 2017'
description: Découvrez comment ouvrir un projet dans un référentiel git ou Azure DevOps à l’aide de Visual Studio 2017.
ms.custom: vs-acquisition, get-started
ms.date: 02/15/2021
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
monikerRange: vs-2017
ms.openlocfilehash: 5543a568f7246d9600ba375d9a1cf19af4cbd2d4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389200"
---
# <a name="tutorial-open-a-project-from-a-repo-in-visual-studio-2017"></a>Didacticiel : ouvrir un projet à partir d’un référentiel dans Visual Studio 2017

Dans ce didacticiel, vous allez utiliser Visual Studio 2017 pour vous connecter à un référentiel pour la première fois, puis ouvrir un projet à partir de celui-ci.

> [!TIP]
> Il existe une nouvelle méthode plus entièrement intégrée pour se connecter à un référentiel GitHub dans [Visual Studio 2019](https://visualstudio.microsoft.com/downloads). Pour plus d’informations, consultez la page [**nouvelle expérience git dans Visual Studio 2019**](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true) .

## <a name="open-a-project-from-a-github-repo-by-using-visual-studio-2017"></a>Ouvrir un projet à partir d’un référentiel GitHub à l’aide de Visual Studio 2017

1. Ouvrez Visual Studio 2017.

1. Dans la barre de menus supérieure, sélectionnez **fichier**  >  **ouvrir**  >  **ouvrir à partir du contrôle de code source**.

   Le volet **Team Explorer - Se connecter** s’affiche.

    ![La fenêtre Team Explorer dans l’IDE de Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Dans la section **dépôts Git locaux** , sélectionnez **cloner**.

    ![Choisir Cloner dans la section Référentiels Git locaux](./media/open-proj-repo-local-git-repo-clone.png)

1. Dans la zone qui indique ***Entrez l’URL d’un référentiel git à cloner** _, tapez ou collez l’URL de votre référentiel, puis appuyez sur _ * ENTER * *. (Vous pouvez recevoir une invite de connexion GitHub. Si c’est le cas, faites-le.)

   Lorsque Visual Studio a cloné votre référentiel, Team Explorer est fermé et l’Explorateur de solutions s’affiche. Le message *Cliquez sur "Solutions et dossiers" ci-dessus pour afficher une liste de solutions* s’affiche. Choisissez **Solutions et dossiers**.

   ![Choisir « Solutions et dossiers » dans l’Explorateur de solutions](./media/open-proj-repo-github-solutions-folders.png)

1. Si un fichier solution est disponible, il apparaît dans le menu contextuel « Solutions et dossiers ». Choisissez-le, Visual Studio ouvre alors votre solution.

   ![Choisir ce que vous souhaitez ouvrir dans la liste déroulante de l’Explorateur de solutions](./media/open-proj-repo-github-solutions-folders-picker.png)

   Si vous n’avez pas de fichier solution (plus précisément, un fichier .sln) dans votre référentiel, le menu contextuel indique « Solutions introuvables ». Vous pouvez toutefois double-cliquer sur n’importe quel fichier dans le menu de dossier pour l’ouvrir dans l’éditeur de code Visual Studio.

### <a name="review-your-work"></a>Passer en revue votre travail

Regardez l’animation suivante pour vérifier le travail que vous avez effectué dans la section précédente.

   ![Animation d’ouverture d’un projet dans un référentiel GitHub à l’aide de Visual Studio](./media/open-project-from-github.gif)

> [!NOTE]
> Pour obtenir des informations spécifiques à Visual Studio 2019, consultez la page [ouvrir un projet à partir d’un référentiel dans Visual studio 2019](tutorial-open-project-from-repo-visual-studio-2019.md) .

## <a name="open-a-project-from-an-azure-devops-repo-by-using-visual-studio-2017"></a>Ouvrir un projet à partir d’un référentiel Azure DevOps à l’aide de Visual Studio 2017

1. Ouvrez Visual Studio 2017.

1. Dans la barre de menus supérieure, sélectionnez **fichier**  >  **ouvrir**  >  **ouvrir à partir du contrôle de code source**.

   Le volet **Team Explorer - Se connecter** s’affiche.

    ![La fenêtre Team Explorer dans l’IDE de Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Voici deux façons de se connecter à votre référentiel Azure DevOps :

      - Dans la section **fournisseurs de services hébergés** , sélectionnez **se connecter...**.

        ![La section Fournisseurs de services hébergés de la fenêtre Team Explorer dans l’IDE de Visual Studio](./media/open-proj-repo-azure-devops.png)

      - Dans la liste déroulante **gérer les connexions** , sélectionnez **se connecter à un projet...**.

        ![La section Gérer les connexions de la fenêtre Team Explorer dans l’IDE de Visual Studio](./media/open-proj-repo-azuredevops-manage-connections.png)

1. Dans la boîte de dialogue **se connecter à un projet** , choisissez le référentiel auquel vous souhaitez vous connecter, puis sélectionnez **cloner**.

      ![La boîte de dialogue « se connecter à un projet » générée à partir de Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Ce que vous voyez dans la zone de liste varie selon les référentiels Azure DevOps auxquels vous avez accès.

1. Lorsque Visual Studio a cloné votre référentiel, Team Explorer est fermé et l’Explorateur de solutions s’affiche. Le message *Cliquez sur "Solutions et dossiers" ci-dessus pour afficher une liste de solutions* s’affiche. Choisissez **Solutions et dossiers**.

      ![La notification « Solutions et les dossiers » de Team Explorer dans Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Un fichier solution (plus précisément, un fichier .sln) apparaît dans le menu contextuel « Solutions et dossiers ». Choisissez-le, Visual Studio ouvre alors votre solution.

   Si vous n’avez pas de fichier solution dans votre référentiel, le menu contextuel indique « Solutions introuvables ». Vous pouvez toutefois double-cliquer sur n’importe quel fichier dans le menu de dossier pour l’ouvrir dans l’éditeur de code Visual Studio.

## <a name="next-steps"></a>Étapes suivantes

Si vous êtes prêt à coder avec Visual Studio 2017, plongez dans les didacticiels spécifiques aux langages suivants :

- [Didacticiels Visual Studio | **C#**](./csharp/index.yml)
- [Didacticiels Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Didacticiels Visual Studio | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Didacticiels Visual Studio | **Python**](../python/index.yml)
- [Didacticiels Visual Studio | **JavaScript**, **TypeScript** et **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Voir aussi

- [Ouvrir un projet à partir d’un référentiel dans Visual Studio 2019](tutorial-open-project-from-repo-visual-studio-2019.md)
- [Nouvelle expérience git dans Visual Studio 2019](../ide/git-with-visual-studio.md)
- [Azure DevOps Services : prise en main de Azure Repos et de Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn : prise en main d’Azure DevOps](/learn/modules/get-started-with-devops/)
