---
title: Publier dans un dossier
ms.date: 04/02/2019
helpviewer_keywords:
- deployment, website, console, publish
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.openlocfilehash: 165cfc38b8289946e0966083785defd18ca87d77
ms.sourcegitcommit: 6993bcb0d2b0067b1b7b7899bfba52c31c70b7e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095409"
---
# <a name="publish-to-a-folder-using-visual-studio-for-mac"></a>Publier dans un dossier à l’aide de Visual Studio pour Mac

Vous pouvez utiliser l’outil publier pour publier une console .NET Core ou des applications ASP.NET Core dans un dossier.

## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2019 pour Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2019) installé avec .net Core activé.
- Une console .NET Core ou un projet de ASP.NET Core. Si vous n’avez pas encore de projet, vous pouvez en [créer un](https://docs.microsoft.com/visualstudio/mac/create-new-projects?view=vsmac-2019).

## <a name="publish-to-folder"></a>Publier sur un dossier

À l’aide de Visual Studio pour Mac vous pouvez publier vos projets .NET Core dans un dossier à l’aide de l’outil de publication. Après la publication dans un dossier, vous pouvez transférer les fichiers vers un autre environnement. Pour publier sur un dossier, effectuez les étapes suivantes.

 1. Dans le panneau Solutions, cliquez avec le bouton droit sur le projet, puis choisissez **Publier**.

    ![Menu contextuel de publication](media/publish-context-menu.png)

 2. Si vous avez déjà publié ce projet, vous voyez le profil de publication apparaître dans le menu. Sélectionnez ce profil de publication pour démarrer le processus de publication.

 3. Pour publier ce projet sur un dossier pour la première fois, sélectionnez **Publier sur un dossier**.

    ![Menu contextuel de publication sur un dossier](media/publish-to-folder-context-menu.png)

 4. La boîte de dialogue **Publier sur un dossier** apparaît. Dans cette boîte de dialogue, vous pouvez personnaliser le dossier sur lequel le projet est publié. Pour ce faire, vous pouvez utiliser le bouton **Parcourir**, ou coller un chemin.

 5. Une fois que vous avez cliqué sur **Publier**, certaines opérations ont lieu. Tout d’abord, un profil de publication est créé. Un profil de publication est un fichier MSBuild importé dans le projet durant le processus de publication. Il contient les propriétés utilisées durant le processus de publication. Ces fichiers sont stockés dans `Properties/PublishProfiles` et ont l’extension `.pubxml`. Le processus de publication démarre ensuite. Vous pouvez superviser la progression en consultant la barre d’état dans Visual Studio pour Mac.

    ![Barre d’état de l’IDE avec l’état de publication](media/publish-to-folder-status-bar.png)

 6. Une fois la publication effectuée, une fenêtre du Finder s’ouvre dans le dossier de publication. Une fois qu’un profil de publication est créé, il est affiché dans le menu contextuel de publication.

    ![Menu contextuel de publication avec le profil de dossier](media/publish-context-menu-with-folder-profile.png)

 7. Pour republier le projet avec les mêmes paramètres, vous pouvez cliquer sur le profil dans le menu contextuel de publication.

## <a name="customize-publish-options"></a>Personnaliser les options de publication

Pour changer le nom du profil de publication (affiché dans le menu contextuel de publication), renommez le fichier de profil de publication. Veillez à ne pas changer l’extension du fichier (`.puxbml`).

Pour changer le chemin du dossier de publication, ouvrez le profil de publication et modifiez la valeur de `publishUrl`.

Pour changer la configuration de build utilisée, changez la propriété `LastUsedBuildConfiguration` dans le profil de publication.
