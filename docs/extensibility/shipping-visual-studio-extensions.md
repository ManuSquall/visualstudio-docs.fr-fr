---
title: Extensions de studio visuel d’expédition Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767bb24bb5cb47f1af1452aa04ebdc91c778e284
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700110"
---
# <a name="shipping-visual-studio-extensions"></a>Publication d’extensions Visual Studio
Une fois que vous avez terminé le développement de votre extension, vous pouvez l’installer sur d’autres machines, la partager avec vos amis et collègues, ou la publier sur le Visual Studio Marketplace. Dans cette section, nous expliquons toutes les choses que vous devez faire afin de publier et de maintenir votre extension: travailler avec des fichiers .vsix, la publication, la localisation et la mise à jour.

## <a name="working-with-vsix-extensions"></a>Travailler avec VSIX Extensions
 Vous pouvez créer des extensions VSIX en créant un projet VSIX vierge, puis en y ajoutant différents modèles d’éléments. Pour plus d’informations, voir [VSIX Project Template](../extensibility/vsix-project-template.md).

 Vous pouvez utiliser le format VSIX pour emballer les modèles de projets, les modèles d’éléments, les VSPackages, les composants du Cadre d’extétiment géré (MEF), les commandes de **boîtes** à outils, les assemblages et les types personnalisés (ce qui inclut les pages de démarrage personnalisées pour Visual Studio 2017). Le format VSIX utilise le déploiement basé sur les fichiers. Pour plus d’informations sur les forfaits VSIX, voir [Anatomie d’un forfait VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 Le format VSIX ne prend pas en charge l’installation de extraits de code. Il n’appuie pas non plus certains autres scénarios tels que l’écriture au Cache de l’Assemblée mondiale (GAC) ou au registre du système. Si vous avez besoin d’écrire au GAC ou au registre de l’installation, vous devez utiliser l’installateur Windows. Pour plus d’informations, voir [Extensions de préparation pour le déploiement de l’installateur Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Publier votre extension au marché des studios visuels
 Vous pouvez distribuer votre extension à d’autres personnes simplement en leur envoyant le fichier .vsix ou en les mettant sur un serveur. Mais la meilleure façon d’obtenir votre code dans les mains de beaucoup de gens est de le mettre sur le [marché Visual Studio](https://marketplace.visualstudio.com/vs). Les extensions Visual Studio Marketplace sont disponibles pour les utilisateurs de Visual Studio par le biais **d’extensions et de mises à jour**. Pour plus d’informations, consultez [Recherche et utilisation des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

 Pour un exemple complet qui montre comment télécharger une extension sur le Visual Studio Marketplace, voir [Walkthrough: Publishing a Visual Studio Extension](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Private Galleries
 Au fur et à mesure que vous développez des contrôles, des modèles et des outils, vous pouvez les partager avec votre organisation en les affichant dans une galerie privée sur votre intranet. Pour plus d’informations, voir [Galeries privées](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Localisation de votre extension
 Si vous prévoyez de libérer votre extension dans différents endroits, vous devriez envisager de la localiser. Pour une explication de ce qui est impliqué, voir [Localisation des forfaits VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Mise à jour et version de votre extension
 Une fois que vous avez publié votre extension, il viendra un moment où vous devez la mettre à jour. Pour savoir comment mettre à jour une extension qui a été publiée sur le visual Studio Marketplace, voir [Comment mettre à jour une extension](../extensibility/how-to-update-a-visual-studio-extension.md).

 Vous pouvez définir votre extension pour prendre en charge plusieurs versions de Visual Studio. Pour plus d’informations, voir [Supporting Multiple Versions of Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Bien démarrer avec le modèle de projet VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Explique comment utiliser le modèle de projet VSIX pour installer un modèle de projet personnalisé.|
|[Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Décrit les composants d’un package VSIX.|
|[Modèle de projet VSIX](../extensibility/vsix-project-template.md)|Fournit des instructions étape par étape sur la façon d’emballer et de publier une extension.|
|[Localisation de packages VSIX](../extensibility/localizing-vsix-packages.md)|Explique comment fournir du texte localisé pour le processus d’installation en utilisant des fichiers extension.vsixlangpack.|
|[Guide pratique pour mettre à jour une extension](../extensibility/how-to-update-a-visual-studio-extension.md)|Décrit comment mettre à jour une extension sur votre système et comment déployer une mise à jour à une extension visual Studio existante.|
|[Guide pratique ajouter une dépendance à un package VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Décrit comment ajouter des références aux paquets de déploiement VSIX.|
|[Préparation d’extensions au déploiement de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Explique comment déployer votre extension avec Windows Installer.|
|[Signature de packages VSIX](../extensibility/signing-vsix-packages.md)|Explique comment signer des forfaits VSIX.|
|[Galeries privées](../extensibility/private-galleries.md)|Explique comment créer des galeries privées pour les extensions.|
|[Prise en charge de plusieurs versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Montre comment avoir votre support d’extension plusieurs versions de Visual Studio.|
|[Recherche de Visual Studio](locating-visual-studio.md)|Décrit comment localiser les instances Visual Studio pour le déploiement d’extension personnalisée.|
