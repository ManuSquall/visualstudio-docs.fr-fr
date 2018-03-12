---
title: Envoi des Extensions Visual Studio | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 543f107081a5cc29ac14f1c2ba2e05924b72e353
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="shipping-visual-studio-extensions"></a>Envoi des Extensions Visual Studio
Une fois que vous avez terminé de développer votre extension, vous pouvez l’installer sur d’autres ordinateurs, le partager avec vos amis et collègues ou le publier sur le Marketplace Visual Studio. Cette section explique tout ce que vous devez faire pour publier et mettre à jour votre extension : utilisation des fichiers .vsix, publication, la localisation et la mise à jour.  
  
## <a name="working-with-vsix-extensions"></a>Utilisation des Extensions VSIX  
 Vous pouvez créer les extensions VSIX par la création d’un projet VSIX vide, d’ajout de modèles d’élément différent à elle. Pour plus d’informations, consultez [modèle de projet VSIX](../extensibility/vsix-project-template.md).  
  
 Vous pouvez utiliser le format VSIX pour les modèles de projet de package, des composants de modèles, des VSPackages, Managed Extensibility Framework (MEF), d’élément **boîte à outils** contrôles, des assemblys et des types personnalisés (Cela inclut les Pages de démarrage personnalisées). Le format VSIX utilise un déploiement basé sur le fichier. Pour plus d’informations sur les packages VSIX, consultez [Anatomie d’un Package VSIX](../extensibility/anatomy-of-a-vsix-package.md).  
  
 Le format VSIX ne prend pas en charge l’installation des extraits de code. Il également ne prend pas en charge certains autres scénarios tels que l’écriture vers le Global Assembly Cache (GAC) ou dans le Registre système. Si vous avez besoin d’écrire dans le GAC ou le Registre de l’installation, vous devez utiliser le programme d’installation de Windows. Pour plus d’informations, consultez [préparation des Extensions de déploiement de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md).  
  
## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Publication de votre Extension pour Visual Studio Marketplace  
 Vous pouvez distribuer votre extension à d’autres personnes simplement par courrier le fichier .vsix ou insérer sur un serveur. Mais la meilleure façon d’obtenir votre code entre les mains d’un grand nombre de personnes consiste à placer dans le [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Extensions de Visual Studio Marketplace sont disponibles pour les utilisateurs de Visual Studio via **Extensions et mises à jour**. Pour plus d’informations, consultez [Recherche et utilisation des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
 Pour obtenir un exemple complet qui montre comment télécharger une extension vers Visual Studio Marketplace, consultez [procédure pas à pas : publication d’une Extension Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
## <a name="private-galleries"></a>Private Galleries  
 Lorsque vous développez des contrôles, des modèles et des outils, vous pouvez les partager avec votre organisation en les publiant dans une galerie privée sur votre intranet. Pour plus d’informations, consultez [Galeries privées](../extensibility/private-galleries.md).  
  
## <a name="localizing-your-extension"></a>Localisation de votre Extension  
 Si vous envisagez de publier votre extension dans les différents paramètres régionaux, vous devez envisager de sa localisation. Pour obtenir une explication de ce qui est impliqué, consultez [localisation des Packages VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="updating-and-versioning-your-extension"></a>Mise à jour et contrôle de version de votre Extension  
 Une fois que vous avez publié votre extension, il arrivera un moment lorsque vous devez mettre à jour. Pour savoir comment mettre à jour une extension qui a été publiée sur le Marketplace Visual Studio, consultez [Comment : mettre à jour une Extension](../extensibility/how-to-update-a-visual-studio-extension.md).  
  
 Vous pouvez définir votre extension pour prendre en charge plusieurs versions de Visual Studio. Pour plus d’informations, consultez [prise en charge de plusieurs Versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Bien démarrer avec le modèle de projet VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Explique comment utiliser le modèle de projet VSIX pour installer un modèle de projet personnalisé.|  
|[Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Décrit les composants d’un package VSIX.|  
|[Modèle de projet VSIX](../extensibility/vsix-project-template.md)|Fournit des instructions détaillées sur la façon d’empaqueter et publier une extension.|  
|[Localisation de packages VSIX](../extensibility/localizing-vsix-packages.md)|Explique comment fournir du texte localisé pour le processus d’installation à l’aide de fichiers extension.vsixlangpack.|  
|[Comment : mettre à jour une Extension](../extensibility/how-to-update-a-visual-studio-extension.md)|Décrit comment mettre à jour une extension sur votre système et comment déployer une mise à jour à une extension Visual Studio.|  
|[Guide pratique ajouter une dépendance à un package VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Décrit comment ajouter des références aux packages de déploiement VSIX.|  
|[Préparation d’extensions pour le déploiement de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Explique comment déployer votre extension de Windows Installer.|  
|[Signature de packages VSIX](../extensibility/signing-vsix-packages.md)|Explique comment signer des packages VSIX.|  
|[Galeries privées](../extensibility/private-galleries.md)|Explique comment créer des galeries privées pour les extensions.|  
|[Prise en charge de plusieurs versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Montre comment votre extension de la prise en charge de plusieurs versions de Visual Studio.|
|[Recherche de Visual Studio](locating-visual-studio.md)|Décrit comment localiser les instances de Visual Studio pour le déploiement de l’extension personnalisée.|
