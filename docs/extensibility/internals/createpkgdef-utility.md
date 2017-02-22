---
title: "Utilitaire de CreatePkgDef | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "définition de package"
  - "créer pkgdef"
  - "pkgdef"
  - "createpkgdef"
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Utilitaire de CreatePkgDef
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilise un fichier .dll d'une extension Visual Studio en tant que paramètre et crée un fichier .pkgdef pour accompagner le fichier .dll. Le fichier .pkgdef contient toutes les informations qui seraient sinon écrite dans le Registre système lorsque l'extension est installée.  
  
> [!NOTE]
>  La plupart des modèles de projet qui sont inclus dans le Kit de développement logiciel Visual Studio automatiquement créer .pkgdef fichiers dans le cadre du processus de génération. Ce document est destiné à ceux qui souhaitent créer manuellement des packages, ou convertir des packages existants pour utiliser un déploiement .pkgdef.  
  
## Syntaxe  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## Arguments  
 \/ out \=`FileName`  
 Obligatoire. Définit le nom du fichier de sortie .pkgdef à```FileName`.  
  
 \/codebase  
 Facultatif. Inscription de force avec l'utilitaire de base de code.  
  
 \/ assembly  
 Inscription de force avec l'utilitaire Assembly.  
  
 `AssemblyPath`  
 Le chemin d'accès du fichier .dll à partir de laquelle vous souhaitez générer le .pkgdef.  
  
## Notes  
 Déploiement de l'extension en utilisant des fichiers .pkgdef remplace la configuration requise du Registre des versions antérieures de Visual Studio.  
  
 Les fichiers .pkgdef doivent être installés dans un des emplacements suivants : %localappdata%\\Microsoft\\Visual Studio\\14.0\\Extensions\\ ou % vsinstalldir%\\Common7\\IDE\\Extensions\\. Si le dossier d'installation est %localappdata%\\Microsoft\\Visual Studio\\14.0\\Extensions\\, l'extension est reconnue par Visual Studio, mais il est désactivée par défaut. L'utilisateur peut activer l'extension à l'aide de **Extensions et mises à jour**. Si le dossier d'installation est % vsinstalldir%\\Common7\\IDE\\Extensions\\, l'extension est activée par défaut.  
  
> [!NOTE]
>  Le **Extensions et mises à jour** outil ne peut pas être utilisé pour accéder à une extension, sauf si elle est installée dans le cadre d'un package VSIX.  
  
## Voir aussi  
 [Utilitaire de CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)