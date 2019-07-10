---
title: Compilation et génération
description: Cet article décrit comment compiler et générer des projets et des solutions dans Visual Studio pour Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: 0165594b4c2d77005c2a9ef921cce457f6f2d0f6
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693123"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Compilation et génération dans Visual Studio pour Mac

Vous pouvez utiliser Visual Studio pour Mac pour générer des applications et créer des assemblys lors du développement de votre projet. Il est important de compiler et de générer votre code régulièrement afin de pouvoir identifier les incompatibilités de type et autres erreurs de compilation.

## <a name="building-from-the-ide"></a>Génération à partir de l'IDE

Vous pouvez utiliser Visual Studio pour Mac pour créer et exécuter des builds instantanément, tout en gardant le contrôle sur les fonctionnalités de génération. Visual Studio pour Mac utilise MSBuild comme système de génération sous-jacent.

Tous les projets et toutes les solutions créées dans l’IDE ont une configuration de build par défaut, qui définit le contexte des builds. Vous pouvez modifier ces configurations ou créer les vôtres. La création ou la modification de ces configurations met automatiquement à jour le fichier projet, qui est ensuite utilisé par MSBuild pour générer votre projet.

Pour plus d’informations sur la génération de projets et de solutions dans l’IDE, consultez le guide [Génération et nettoyage des projets et des solutions](building-and-cleaning-projects-and-solutions.md).

Vous pouvez aussi utiliser Visual Studio pour Mac pour :

* Changer le chemin de la sortie. Vous modifiez ce chemin dans les options de votre projet :

    ![Changer le chemin de la sortie](media/compiling-and-building-image4.png)

* Changer le niveau de détail de la sortie de la génération :

    ![Changer le niveau de détail de la génération](media/compiling-and-building-image5.png)

* Ajouter des commandes personnalisées avant, pendant ou après la génération ou le nettoyage :

    ![Ajouter des commandes personnalisées](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>Génération à partir de la ligne de commande

Vous pouvez utiliser le moteur de génération MSBuild pour générer des applications via la ligne de commande.

Pour plus d’informations sur l’utilisation de MSBuild, consultez [MSBuild](/visualstudio/msbuild/msbuild).

## <a name="building-from-azure-pipelines"></a>Génération à partir d’Azure Pipelines

* [Générer votre application Xamarin](/vsts/pipelines/apps/mobile/xamarin?view=vsts&tabs=vsts)
* [Intégration continue avec Xamarin](https://developer.xamarin.com/guides/cross-platform/ci/)

## <a name="see-also"></a>Voir aussi

- [Compiler et générer (Visual Studio sur Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)