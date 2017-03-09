---
title: "MSBuild Error MSB3185 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.NoEntryPoint"
helpviewer_keywords: 
  - "MSB3185"
ms.assetid: 032c63c5-d662-42ba-84e1-e3ccca8cee05
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3185
**MSB3185 : Paramètre EntryPoint non spécifié pour le manifeste.**  
  
 Cette erreur est générée lorsqu'un manifeste ne spécifie pas de point d'entrée.  Elle peut s'appliquer à la fois au manifeste d'application et de déploiement.  
  
### Pour corriger cette erreur  
  
-   Si vous utilisez la tâche GenerateApplicationManifest, veillez à spécifier un point d'entrée valide ou à attribuer à la propriété TargetFrameworkVersion la "v3.5" ou toute valeur supérieure.  Pour un manifeste d'application, un point d'entrée valide est un fichier .exe.  
  
-   Si vous utilisez la tâche GenerateDeploymentManifest, veillez à spécifier des points d'entrée valides dans vos manifestes.  Pour un manifeste de déploiement, un point d'entrée valide est un manifeste d'application.  
  
## Voir aussi  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 [Page Publier, Concepteur de projets](../ide/reference/publish-page-project-designer.md)   
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)   
 [MSBuild Error MSB3116](../misc/msbuild-error-msb3116.md)   
 [MSBuild Error MSB3117](/visual-cpp/misc/msbuild-error-msb3117)   
 [MSBuild Error MSB3118](../misc/msbuild-error-msb3118.md)   
 [MSBuild Error MSB3174](/visual-cpp/misc/msbuild-error-msb3174)