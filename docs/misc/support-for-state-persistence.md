---
title: "Prise en charge de la persistance de l’&#233;tat | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "persistance de l’état, prise en charge de managed package framework"
  - "managed package framework, prise en charge de la persistance de l’état"
  - "état, persistance"
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
caps.handback.revision: 15
manager: "douge"
---
# Prise en charge de la persistance de l’&#233;tat
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] peut conserver l'état des objets communs.  Par exemple, la solution et les propriétés du projet sont stockées sur et restaurées à partir de la solution et fichiers de projet.  Les paramètres utilisateur peuvent être exportés à et importés à partir de fichiers de paramètres.  
  
 VSPackages reposent généralement sur le stockage local, dans la base de registres ou dans le dossier application pour l'utilisateur actuel ou l'ordinateur.  Les valeurs qui requièrent une petite quantité d'espace pour le stockage, tel que les entiers et les chaînes, sont stockées en général dans la base de registres.  Les valeurs qui requièrent une grande quantité d'espace de stockage, tel que des images, sont stockées dans un fichier.  Le chemin d'accès du fichier peut être stocké dans la base de registres.  le mécanisme de persistance doit avoir l'autorisation d'accéder au stockage local.  
  
## Prise en charge de localiser le stockage local  
 La classe d' <xref:Microsoft.VisualStudio.Shell.Package> fournit la prise en charge pour localiser des informations d'état dans le dossier de base de registres ou de données d'application pour l'utilisateur actuel ou l'ordinateur.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 Retourne le chemin d'accès de la racine de Registre de l'ordinateur local pour [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], par exemple, HKEY\_LOCAL\_MACHINE \\Software\\Microsoft\\VisualStudio\\8.0Exp.  
  
 La racine de Registre locale est obtenue du service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> .  S'il n'est pas disponible, elle est obtenu à partir de l'attribut d' <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> du VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 Retourne le chemin d'accès de la racine de Registre de l'utilisateur en cours \(par ordinateur\) pour [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], par exemple, HKEY\_CURRENT\_USER \\Software\\Microsoft\\VisualStudio\\8.0Exp.  
  
 La racine de Registre locale est obtenue du service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> .  S'il n'est pas disponible, elle est obtenu à partir de l'attribut de DefaultLocalRegistryRoot du VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Retourne le chemin d'accès du dossier qui sert de référentiel commune aux données de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour l'utilisateur itinérant actuel, par exemple, C : \\Documents and Settings \\*YourAccountName*\\Application Data\\Microsoft\\VisualStudio\\8.0Exp.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Retourne le chemin d'accès du dossier qui sert de référentiel commune aux données de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour l'utilisateur non\-errant actuel, par exemple, C : \\Documents and Settings \\*YourAccountName*\\Local Settings\\Application Data\\Microsoft\\VisualStudio\\8.0Exp.  
  
## Voir aussi  
 [État du VSPackage](/visual-cpp/misc/vspackage-state)