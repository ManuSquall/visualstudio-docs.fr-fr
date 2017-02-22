---
title: "Pr&#233;paration des Extensions pour le d&#233;ploiement de Windows Installer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSIX et msi"
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Pr&#233;paration des Extensions pour le d&#233;ploiement de Windows Installer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous ne pouvez pas utiliser un package Windows Installer \(MSI\) pour déployer un package VSIX. Toutefois, vous pouvez extraire le contenu d’un package VSIX pour le déploiement du MSI. Ce document montre comment préparer un projet dont la sortie par défaut est un package VSIX pour inclusion dans un projet d’installation.  
  
## Préparation d’un projet d’Extension pour le déploiement de Windows Installer  
 Effectuez ces étapes dans les nouveaux projets d’extension avant d’ajouter à un projet d’installation.  
  
#### Pour préparer un projet d’extension pour le déploiement de Windows Installer  
  
1.  Créez un VSPackage, composant MEF, éditeur ornement ou autre type de projet d’extensibilité qui inclut un manifeste VSIX.  
  
2.  Ouvrez le manifeste VSIX dans l’éditeur de code.  
  
3.  Définir l’élément InstalledByMsi du manifeste VSIX la valeur `true`. Pour plus d’informations sur le manifeste VSIX, consultez [Référence du schéma 2.0 Extension VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Cela empêche le programme d’installation de l’extension VSIX installer le composant.  
  
4.  Cliquez sur le projet dans **l’Explorateur de solutions** sur **propriétés**.  
  
5.  Sélectionnez le **VSIX** onglet.  
  
6.  Activez la case à cocher **contenu VSIX de copie à l’emplacement suivant** et tapez le chemin d’accès où le projet d’installation utilisera les fichiers.  
  
## Extraction des fichiers à partir d’un Package VSIX  
 Procédez comme suit pour ajouter le contenu d’un package VSIX existant à un projet d’installation lorsque vous n’avez pas les fichiers sources.  
  
#### Pour extraire des fichiers à partir d’un package VSIX  
  
1.  Renommez le. Fichier VSIX qui contient l’extension de *nom de fichier*.vsix pour *nom de fichier*.zip.  
  
2.  Copiez le contenu du fichier .zip dans un répertoire.  
  
3.  Supprimer le fichier \[Content\_types\] .xml à partir du répertoire.  
  
4.  Modifiez le manifeste VSIX, comme illustré dans la procédure précédente.  
  
5.  Ajouter les fichiers restants à votre projet d’installation.  
  
## Voir aussi  
 [Visual Studio Installer Deployment](http://msdn.microsoft.com/fr-fr/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Walkthrough: Creating a Custom Action](http://msdn.microsoft.com/fr-fr/4bd4b63a-2b91-431e-839c-5752443f0eaf)