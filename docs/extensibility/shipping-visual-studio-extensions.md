---
title: Expédition des extensions Visual Studio | Microsoft Docs
description: Apprenez à publier et à gérer votre extension du kit de développement logiciel (SDK) Visual Studio, y compris l’utilisation des fichiers. vsix, la publication, la localisation et la mise à jour.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 812fc4f4e2f8dcf54876e2764f0c091f16348496
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97716001"
---
# <a name="shipping-visual-studio-extensions"></a>Publication d’extensions Visual Studio
Une fois que vous avez terminé le développement de votre extension, vous pouvez l’installer sur d’autres machines, la partager avec vos amis et vos collègues, ou la publier sur le Visual Studio Marketplace. Dans cette section, nous expliquons toutes les choses que vous devez effectuer pour publier et gérer votre extension : utilisation des fichiers. vsix, publication, localisation et mise à jour.

## <a name="working-with-vsix-extensions"></a>Utilisation des extensions VSIX
 Vous pouvez créer des extensions VSIX en créant un projet VSIX vide, puis en y ajoutant différents modèles d’élément. Pour plus d’informations, consultez [modèle de projet VSIX](../extensibility/vsix-project-template.md).

 Vous pouvez utiliser le format VSIX pour empaqueter des modèles de projet, des modèles d’élément, des VSPackages, des composants de Managed Extensibility Framework (MEF), des contrôles de **boîte à outils** , des assemblys et des types personnalisés (y compris des pages de démarrage personnalisées pour Visual Studio 2017). Le format VSIX utilise le déploiement basé sur des fichiers. Pour plus d’informations sur les packages VSIX, consultez [anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 Le format VSIX ne prend pas en charge l’installation des extraits de code. Il ne prend pas non plus en charge certains autres scénarios, tels que l’écriture dans le global assembly cache (GAC) ou dans le registre système. Si vous devez écrire dans le GAC ou dans le registre de l’installation, vous devez utiliser la Windows Installer. Pour plus d’informations, consultez [préparation des extensions pour le déploiement de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Publication de votre extension sur le Visual Studio Marketplace
 Vous pouvez distribuer votre extension à d’autres personnes simplement en les envoyant au fichier. VSIX ou en les plaçant sur un serveur. Mais la meilleure façon de faire en sorte que votre code soit chargé de nombreuses personnes consiste à la placer sur le [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Les extensions de Visual Studio Marketplace sont disponibles pour les utilisateurs de Visual Studio via **des extensions et des mises à jour**. Pour plus d’informations, consultez [Recherche et utilisation des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

 Pour obtenir un exemple complet qui montre comment télécharger une extension vers le Visual Studio Marketplace, consultez [procédure pas à pas : publication d’une extension Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Private Galleries
 Lorsque vous développez des contrôles, des modèles et des outils, vous pouvez les partager avec votre organisation en les publiant dans une galerie privée sur votre intranet. Pour plus d’informations, consultez [galeries privées](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Localisation de votre extension
 Si vous envisagez de publier votre extension dans des paramètres régionaux différents, vous devez envisager de la localiser. Pour obtenir une explication de ce qui est impliqué, consultez [localisation des packages VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Mise à jour et contrôle de version de votre extension
 Une fois que vous avez publié votre extension, il y aura une heure à laquelle vous devrez la mettre à jour. Pour savoir comment mettre à jour une extension qui a été publiée sur le Visual Studio Marketplace, consultez [Comment : mettre à jour une extension](../extensibility/how-to-update-a-visual-studio-extension.md).

 Vous pouvez définir votre extension pour prendre en charge plusieurs versions de Visual Studio. Pour plus d’informations, consultez [prise en charge de plusieurs versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Bien démarrer avec le modèle de projet VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Explique comment utiliser le modèle de projet VSIX pour installer un modèle de projet personnalisé.|
|[Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Décrit les composants d’un package VSIX.|
|[Modèle de projet VSIX](../extensibility/vsix-project-template.md)|Fournit des instructions pas à pas pour empaqueter et publier une extension.|
|[Localisation de packages VSIX](../extensibility/localizing-vsix-packages.md)|Explique comment fournir du texte localisé pour le processus d’installation à l’aide de fichiers extension. vsixlangpack.|
|[Guide pratique pour mettre à jour une extension](../extensibility/how-to-update-a-visual-studio-extension.md)|Décrit comment mettre à jour une extension sur votre système et comment déployer une mise à jour sur une extension Visual Studio existante.|
|[Guide pratique ajouter une dépendance à un package VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Décrit comment ajouter des références aux packages de déploiement VSIX.|
|[Préparation d’extensions au déploiement de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Explique comment déployer votre extension avec Windows Installer.|
|[Signature de packages VSIX](../extensibility/signing-vsix-packages.md)|Explique comment signer des packages VSIX.|
|[Galeries privées](../extensibility/private-galleries.md)|Explique comment créer des galeries privées pour les extensions.|
|[Prise en charge de plusieurs versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Montre comment votre extension prend en charge plusieurs versions de Visual Studio.|
|[Recherche de Visual Studio](locating-visual-studio.md)|Décrit comment localiser des instances de Visual Studio pour le déploiement d’extensions personnalisées.|
