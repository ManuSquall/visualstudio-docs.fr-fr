---
title: "Utilitaire de RegPkg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "regpkg, utilitaire d'enregistrement"
  - "inscription, utilitaire de regpkg"
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Utilitaire de RegPkg
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  La meilleure méthode pour enregistrer des packages dans Visual Studio est en utilisant des fichiers .pkgdef. Ainsi, pour le déploiement de l'extension sans avoir à accéder au Registre système, qui est nécessaire pour le déploiement VSIX. Pkgdef fichiers sont créés à l'aide de la [Utilitaire de CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Pour plus d'informations sur le déploiement du package Visual Studio, consultez [Envoi des Extensions Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 L'utilitaire RegPkg.exe enregistre un VSPackage avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et le prépare pour le déploiement. Cet utilitaire est utilisé en arrière\-plan pendant le développement VSPackage. Il s'exécute dans le cadre du processus de génération afin que vous pouvez générer et exécuter un VSPackage dans la ruche expérimentale.  
  
 RegPkg peuvent générer des scripts de Registre système dans plusieurs formats. Vous pouvez incorporer ces scripts dans les projets de déploiement tels que les projets .msi ou des fichiers de l'ensemble d'outils XML de Windows Installer.  
  
 RegPkg.exe est généralement situé à \<*chemin d'installation de Visual Studio SDK*\> \\VisualStudioIntegration\\Tools\\Bin\\RegPkg.exe. RegPkg suit cette syntaxe :  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 \/root:root  
 Effectue le processus d'inscription spécifié  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] racine.  
  
 \/regfile:filename  
 Crée un fichier .reg, plutôt que de mettre à jour le Registre.  Ne peut pas être utilisé avec \/vrgfile ou \/rgsfile ou \/wixfile.  
  
 \/rgsfile:filename  
 Crée un fichier .rgs plutôt que de mettre à jour le Registre.  Ne peut pas être utilisé avec \/vrgfile \/regfile ou \/wixfile.  
  
 \/vrgfile:filename  
 Crée un fichier .vrg au lieu de mettre à jour le Registre.  Ne peut pas être utilisé avec \/regfile ou \/rgsfile ou \/wixfile.  
  
 \/RGM  
 Crée un fichier .rgm en plus du fichier rgs.  Doit être combinée avec \/rgsfile.  
  
 \/wixfile:filename  
 Crée un fichier compatible ensemble d'outils XML de Windows Installer, plutôt que de mettre à jour le Registre.  Ne peut pas être utilisé avec \/regfile ou \/rgsfile ou \/vrgfile.  
  
 \/codebase  
 Inscription de force avec base de code plutôt que d'Assembly.  
  
 \/ assembly  
 Inscription de force avec l'Assembly plutôt que de base de code.  
  
 \/unregister  
 Annule l'inscription de ce package.  Ne peut pas être utilisé.  
  
 avec \/regfile ou \/vrgfile ou \/rgsfile ou \/wixfile.  
  
## Voir aussi  
 [Publication d’un produit](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Inscription de package de RegPkg de résolution des problèmes](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)