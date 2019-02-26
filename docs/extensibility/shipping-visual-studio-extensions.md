---
title: Proposent des Extensions de Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ea2217614ed27a98281cce7a3d34b72f74ae803
ms.sourcegitcommit: 1c8e07b98fc0a44b5ab90bcef77d9fac7b3eb452
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2019
ms.locfileid: "56796593"
---
# <a name="shipping-visual-studio-extensions"></a>Publication d’extensions Visual Studio
Une fois que vous avez terminé de développer votre extension, vous pouvez l’installer sur d’autres ordinateurs, partager avec vos amis et collègues ou publiez-la sur la place de marché Visual Studio. Dans cette section, nous vous expliquons tout ce que vous devez effectuer pour publier et mettre à jour votre extension : utilisation des fichiers .vsix, publication, la localisation et la mise à jour.

## <a name="working-with-vsix-extensions"></a>Utilisation des Extensions VSIX
 Vous pouvez créer un extensions VSIX en créant un projet VSIX vide et puis en ajoutant les modèles d’élément différent pour elle. Pour plus d’informations, consultez [modèle de projet VSIX](../extensibility/vsix-project-template.md).

 Vous pouvez utiliser le format VSIX pour empaqueter des modèles de projet, des composants de modèles, des VSPackages, Managed Extensibility Framework (MEF), d’élément **boîte à outils** contrôles, des assemblys et types personnalisés (Cela inclut les Pages de démarrage personnalisées pour Visual Studio 2017). Le format VSIX utilise un déploiement basé sur le fichier. Pour plus d’informations sur les packages VSIX, consultez [Anatomie d’un Package VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 Le format VSIX ne prend pas en charge l’installation d’extraits de code. Elle également ne prend pas en charge certains autres scénarios tels que d’écriture vers le Global Assembly Cache (GAC) ou dans le Registre système. Si vous avez besoin écrire dans le GAC ou le Registre dans l’installation, vous devez utiliser le programme d’installation de Windows. Pour plus d’informations, consultez [préparation des Extensions pour le déploiement d’installation Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Publication de votre Extension à la place de marché Visual Studio
 Vous pouvez distribuer votre extension à d’autres personnes en tout simplement distribuer ces autocollants le fichier .vsix ou en plaçant sur un serveur. Mais la meilleure façon d’obtenir votre code entre les mains d’un grand nombre de personnes consiste à placer sur le [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Extensions de Visual Studio Marketplace sont disponibles aux utilisateurs de Visual Studio via **Extensions et mises à jour**. Pour plus d’informations, consultez [Recherche et utilisation des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

 Pour obtenir un exemple complet qui montre comment charger une extension à la place de marché Visual Studio, consultez [procédure pas à pas : Publication d’une Extension Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Private Galleries
 Lorsque vous développez des contrôles, des modèles et des outils, vous pouvez les partager avec votre organisation en publiant sur une galerie privée sur votre intranet. Pour plus d’informations, consultez [Galeries privées](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Localisation de votre Extension
 Si vous avez l’intention de mise en production de votre extension dans les différents paramètres régionaux, vous devez envisager sa localisation. Pour obtenir une explication de ce qui est impliqué, consultez [localisation des Packages VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>La mise à jour et contrôle de version de votre Extension
 Une fois que vous avez publié votre extension, il arrivera un moment lorsque vous devez mettre à jour. Pour savoir comment mettre à jour une extension qui a été publiée sur la place de marché Visual Studio, consultez [Comment : Mettre à jour une Extension](../extensibility/how-to-update-a-visual-studio-extension.md).

 Vous pouvez définir votre extension pour prendre en charge plusieurs versions de Visual Studio. Pour plus d’informations, consultez [prenant en charge plusieurs Versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Bien démarrer avec le modèle de projet VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Explique comment utiliser le modèle de projet VSIX pour installer un modèle de projet personnalisé.|
|[Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Décrit les composants d’un package VSIX.|
|[Modèle de projet VSIX](../extensibility/vsix-project-template.md)|Fournit des instructions détaillées sur la façon d’empaqueter et publier une extension.|
|[Localisation de packages VSIX](../extensibility/localizing-vsix-packages.md)|Explique comment fournir un texte localisé pour le processus d’installation à l’aide de fichiers extension.vsixlangpack.|
|[Guide pratique pour Mettre à jour une Extension](../extensibility/how-to-update-a-visual-studio-extension.md)|Décrit comment mettre à jour une extension sur votre système et comment déployer une mise à jour à une extension Visual Studio.|
|[Guide pratique pour Ajouter une dépendance à un Package VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Décrit comment ajouter des références aux packages de déploiement VSIX.|
|[Préparation d’extensions pour le déploiement de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Explique comment déployer votre extension avec le programme d’installation de Windows.|
|[Signature de packages VSIX](../extensibility/signing-vsix-packages.md)|Explique comment signer des packages VSIX.|
|[Galeries privées](../extensibility/private-galleries.md)|Explique comment créer des galeries privées pour les extensions.|
|[Prise en charge de plusieurs versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Montre comment votre extension de la prise en charge plusieurs versions de Visual Studio.|
|[Recherche de Visual Studio](locating-visual-studio.md)|Décrit comment localiser les instances de Visual Studio pour le déploiement de l’extension personnalisée.|
