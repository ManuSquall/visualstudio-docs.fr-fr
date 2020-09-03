---
title: Publier dans un dossier
ms.date: 01/22/2019
helpviewer_keywords:
- deployment, website
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.topic: how-to
ms.openlocfilehash: 4fe8f7e99f950bbc7a393712d0831f5a4a229481
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85950065"
---
# <a name="publish-a-web-app-to-a-folder-using-visual-studio-for-mac"></a>Publier une application web sur un dossier à l’aide de Visual Studio pour Mac

Vous pouvez utiliser l’outil Publier pour publier des applications ASP.NET Core sur un dossier.

## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2017 pour Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2017) installé et ASP.NET Core activé.
- Un projet ASP.NET Core. Si vous n’avez pas encore de projet, vous pouvez en [créer un](/visualstudio/mac/create-new-projects?view=vsmac-2017).

## <a name="publish-to-folder"></a>Publier sur un dossier

Avec Visual Studio pour Mac, vous pouvez publier vos projets ASP.NET Core sur un dossier via l’outil Publier. Après avoir effectué la publication sur un dossier, vous pouvez transférer les fichiers sur votre serveur web pour le placer dans un autre environnement. Pour publier sur un dossier, effectuez les étapes suivantes.

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