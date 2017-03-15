---
title: "MSBuild Error MSB3118 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.UseApplicationTrustInvalidFrameworkVersion"
helpviewer_keywords: 
  - "MSB3118"
ms.assetid: 9bf5b430-0cfb-4da5-a7f7-04d69f20cce1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3118
**MSB3118: L'application est configurée pour utiliser le niveau de confiance mais TargetFrameworkVersion n'a pas la valeur v3.5.**  
  
 Cette erreur se produit lorsque vous affectez la valeur `True` à la propriété <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.UseApplicationTrust%2A> et que vous définissez une version inférieure à `v3.5` \(par exemple, `v2.0`\) pour la propriété <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>.  
  
### Pour corriger cette erreur  
  
-   Affectez à la propriété <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> la valeur `v3.5` ou supérieure.  
  
## Voir aussi  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.UseApplicationTrust%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.UseApplicationTrust%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 [Page Publier, Concepteur de projets](../ide/reference/publish-page-project-designer.md)   
 [MSBuild Error MSB3116](../misc/msbuild-error-msb3116.md)   
 [MSBuild Error MSB3117](/visual-cpp/misc/msbuild-error-msb3117)   
 [MSBuild Error MSB3119](../misc/msbuild-error-msb3119.md)   
 [MSBuild Error MSB3174](/visual-cpp/misc/msbuild-error-msb3174)   
 [MSBuild Error MSB3185](../misc/msbuild-error-msb3185.md)