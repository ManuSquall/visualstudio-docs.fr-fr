---
title: "Envoi des Extensions Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Déploiement VSIX"
  - "déploiement VSIX"
  - "DLL satellites, de packages VSIX"
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Envoi des Extensions Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Après avoir terminé le développement de votre extension, vous pouvez installer sur d'autres ordinateurs, partager avec vos amis et collègues ou publiez\-la sur la galerie Visual Studio. Dans cette section, nous vous expliquons tout ce que vous devez effectuer afin de publier et gérer votre extension : utilisation des fichiers .vsix, publication, la localisation et la mise à jour.  
  
## Utilisation des Extensions VSIX  
 Vous pouvez créer les extensions VSIX en créant un projet VSIX vide et lui ajoutant les modèles d'élément différent. Pour plus d'informations, consultez [Modèle de projet VSIX](../extensibility/vsix-project-template.md).  
  
 Vous pouvez utiliser le format VSIX pour empaqueter des modèles de projet, des composants de Managed Extensibility Framework \(MEF\) les VSPackages, modèles, d'élément **boîte à outils** contrôles, des assemblys et des types personnalisés \(y compris les Pages de démarrage personnalisées\). Le format VSIX utilise un déploiement basé sur un fichier. Pour plus d'informations sur les packages VSIX, consultez [Anatomie d'un Package VSIX](../extensibility/anatomy-of-a-vsix-package.md).  
  
 Le format VSIX ne prend pas en charge l'installation d'extraits de code. Elle aussi ne prend pas en charge certains autres scénarios tels que l'écriture vers le Global Assembly Cache \(GAC\) ou dans le Registre système. Si vous avez besoin écrire dans le GAC ou le Registre de l'installation, vous devez utiliser le programme d'installation de Windows. Pour plus d'informations, consultez [Préparation des Extensions pour le déploiement de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md).  
  
## Publication de votre Extension vers la galerie Visual Studio  
 Vous pouvez distribuer votre extension à d'autres personnes simplement par courrier le fichier .vsix ou insérer sur un serveur. Mais la meilleure façon d'obtenir le code entre les mains d'un grand nombre de personnes consiste à placer dans le [la galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847). Extensions de la galerie Visual Studio sont disponibles pour les utilisateurs de Visual Studio via **Extensions et mises à jour**. Pour plus d'informations, consultez [Recherche et utilisation des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
 Pour obtenir un exemple complet qui montre comment télécharger une extension vers la galerie Visual Studio, consultez [Procédure pas à pas : Publication d'une Extension Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
## Les galeries privées  
 Lorsque vous développez des contrôles, des modèles et des outils, vous pouvez les partager avec votre organisation, en les envoyant à une galerie privée sur votre intranet. Pour plus d'informations, consultez [Les galeries privées](../extensibility/private-galleries.md).  
  
## Localisation de votre Extension  
 Si vous prévoyez de publier votre extension dans les différents paramètres régionaux, vous devez envisager de sa localisation. Pour obtenir une explication de ce qui est impliqué, consultez [Localisation de Packages VSIX](../extensibility/localizing-vsix-packages.md).  
  
## Mise à jour et contrôle de version de votre Extension  
 Une fois que vous avez publié votre extension, il arrivera un moment lorsque vous devez mettre à jour. Pour savoir comment mettre à jour une extension qui a été publiée sur la galerie Visual Studio, consultez [Comment : mettre à jour une Extension](../extensibility/how-to-update-a-visual-studio-extension.md).  
  
 Vous pouvez définir votre extension pour prendre en charge plusieurs versions de Visual Studio. Pour plus d'informations, consultez [Prise en charge de plusieurs Versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Mise en route avec le modèle de projet VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Explique comment utiliser le modèle de projet VSIX pour installer un modèle de projet personnalisé.|  
|[Anatomie d'un Package VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Décrit les composants d'un package VSIX.|  
|[Modèle de projet VSIX](../extensibility/vsix-project-template.md)|Fournit des instructions détaillées sur la façon d'empaqueter et publier une extension.|  
|[Localisation de Packages VSIX](../extensibility/localizing-vsix-packages.md)|Explique comment fournir du texte localisé pour le processus d'installation à l'aide de fichiers extension.vsixlangpack.|  
|[Comment : mettre à jour une Extension](../extensibility/how-to-update-a-visual-studio-extension.md)|Décrit comment mettre à jour une extension sur votre système et comment déployer une mise à jour à une extension Visual Studio.|  
|[Comment : ajouter une dépendance à un Package VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Décrit comment ajouter des références aux packages de déploiement VSIX.|  
|[Préparation des Extensions pour le déploiement de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Explique comment déployer votre extension avec Windows Installer.|  
|[Signature de Packages VSIX](../extensibility/signing-vsix-packages.md)|Explique comment signer les packages VSIX.|  
|[Les galeries privées](../extensibility/private-galleries.md)|Explique comment créer des galeries privées pour les extensions.|  
|[Prise en charge de plusieurs Versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Montre comment votre extension de la prise en charge de plusieurs versions de Visual Studio.|