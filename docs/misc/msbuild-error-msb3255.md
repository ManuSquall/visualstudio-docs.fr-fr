---
title: "Erreur MSBuild MSB3255 | Microsoft Docs"
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
  - "MSB3255"
ms.assetid: baac844e-a662-4421-bed1-2bc98f2e1cdf
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erreur MSBuild MSB3255
**MSB3255 : Impossible de trouver des fichiers de sous\-ensembles de version cible du .Net Framework dans les répertoires de version cible du .Net Framework ou aux emplacements spécifiés dans InstalledAssemblySubsetTables.**  
  
 Cette erreur se produit lorsqu'un nom est passé dans la propriété <xref:Microsoft.Build.Tasks.ResolveAssemblyReference.FullTargetFrameworkSubsetNames%2A>, mais qu'un sous\-ensemble avec ce nom est introuvable.  
  
 Le [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] est un sous\-ensemble de la bibliothèque runtime [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 complète.  Pour plus d'informations sur le [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)], consultez [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
 Procédures  
  
### Pour corriger cette erreur  
  
-   Placez une copie du fichier de sous\-ensemble dans le dossier d'infrastructure cible ou dans l'un des emplacements spécifiés dans <xref:Microsoft.Build.Tasks.ResolveAssemblyReference.InstalledAssemblySubsetTables%2A>.  
  
## Voir aussi  
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)