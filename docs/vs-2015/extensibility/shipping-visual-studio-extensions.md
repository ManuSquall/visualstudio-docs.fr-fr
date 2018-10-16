---
title: Proposent des Extensions de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ac367f2482a6b8bc5b5b25fca72e8ca05e1f58b7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260175"
---
# <a name="shipping-visual-studio-extensions"></a>Publication d’extensions Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Remarque**: la galerie Visual Studio est remplacée par la place de marché Visual Studio. Consultez la dernière version de cette rubrique pour plus d’informations.

  
Une fois que vous avez terminé de développer votre extension, vous pouvez l’installer sur d’autres ordinateurs, partager avec vos amis et collègues ou publiez-la sur la galerie Visual Studio. Dans cette section, nous vous expliquons tout ce que vous devez effectuer pour publier et mettre à jour votre extension : utilisation des fichiers .vsix, publication, la localisation et la mise à jour.  
  
## <a name="working-with-vsix-extensions"></a>Utilisation des Extensions VSIX  
 Vous pouvez créer un extensions VSIX en créant un projet VSIX vide et puis en ajoutant les modèles d’élément différent pour elle. Pour plus d’informations, consultez [modèle de projet VSIX](../extensibility/vsix-project-template.md).  
  
 Vous pouvez utiliser le format VSIX pour empaqueter des modèles de projet, des composants de modèles, des VSPackages, Managed Extensibility Framework (MEF), d’élément **boîte à outils** contrôles, des assemblys et types personnalisés (y compris les Pages de démarrage personnalisées). Le format VSIX utilise un déploiement basé sur le fichier. Pour plus d’informations sur les packages VSIX, consultez [Anatomie d’un Package VSIX](../extensibility/anatomy-of-a-vsix-package.md).  
  
 Le format VSIX ne prend pas en charge l’installation d’extraits de code. Elle également ne prend pas en charge certains autres scénarios tels que d’écriture vers le Global Assembly Cache (GAC) ou dans le Registre système. Si vous avez besoin écrire dans le GAC ou le Registre dans l’installation, vous devez utiliser le programme d’installation de Windows. Pour plus d’informations, consultez [préparation des Extensions pour le déploiement d’installation Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md).  
  
## <a name="publishing-your-extension-to-the-visual-studio-gallery"></a>Publication de votre Extension dans la galerie Visual Studio  
 Vous pouvez distribuer votre extension à d’autres personnes en tout simplement distribuer ces autocollants le fichier .vsix ou en plaçant sur un serveur. Mais la meilleure façon d’obtenir votre code entre les mains d’un grand nombre de personnes consiste à placer sur le [galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847). Extensions de la galerie Visual Studio sont disponibles aux utilisateurs de Visual Studio via **Extensions et mises à jour**. Pour plus d’informations, consultez [Recherche et utilisation des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
 Pour obtenir un exemple complet qui montre comment télécharger une extension vers la galerie Visual Studio, consultez [procédure pas à pas : publication d’une Extension Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
## <a name="private-galleries"></a>Private Galleries  
 Lorsque vous développez des contrôles, des modèles et des outils, vous pouvez les partager avec votre organisation en publiant sur une galerie privée sur votre intranet. Pour plus d’informations, consultez [Galeries privées](../extensibility/private-galleries.md).  
  
## <a name="localizing-your-extension"></a>Localisation de votre Extension  
 Si vous avez l’intention de mise en production de votre extension dans les différents paramètres régionaux, vous devez envisager sa localisation. Pour obtenir une explication de ce qui est impliqué, consultez [localisation des Packages VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="updating-and-versioning-your-extension"></a>La mise à jour et contrôle de version de votre Extension  
 Une fois que vous avez publié votre extension, il arrivera un moment lorsque vous devez mettre à jour. Pour savoir comment mettre à jour une extension qui a été publiée sur la galerie Visual Studio, consultez [Comment : mettre à jour une Extension](../extensibility/how-to-update-a-visual-studio-extension.md).  
  
 Vous pouvez définir votre extension pour prendre en charge plusieurs versions de Visual Studio. Pour plus d’informations, consultez [prenant en charge plusieurs Versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Bien démarrer avec le modèle de projet VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Explique comment utiliser le modèle de projet VSIX pour installer un modèle de projet personnalisé.|  
|[Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Décrit les composants d’un package VSIX.|  
|[Modèle de projet VSIX](../extensibility/vsix-project-template.md)|Fournit des instructions détaillées sur la façon d’empaqueter et publier une extension.|  
|[Localisation de packages VSIX](../extensibility/localizing-vsix-packages.md)|Explique comment fournir un texte localisé pour le processus d’installation à l’aide de fichiers extension.vsixlangpack.|  
|[Guide pratique pour mettre à jour une extension](../extensibility/how-to-update-a-visual-studio-extension.md)|Décrit comment mettre à jour une extension sur votre système et comment déployer une mise à jour à une extension Visual Studio.|  
|[Guide pratique ajouter une dépendance à un package VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Décrit comment ajouter des références aux packages de déploiement VSIX.|  
|[Préparation d’extensions pour le déploiement de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Explique comment déployer votre extension avec le programme d’installation de Windows.|  
|[Signature de packages VSIX](../extensibility/signing-vsix-packages.md)|Explique comment signer des packages VSIX.|  
|[Galeries privées](../extensibility/private-galleries.md)|Explique comment créer des galeries privées pour les extensions.|  
|[Prise en charge de plusieurs versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Montre comment votre extension de la prise en charge plusieurs versions de Visual Studio.|

