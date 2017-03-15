---
title: "Erreur MSBuild MSB3254 | Microsoft Docs"
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
  - "MSB3254"
ms.assetid: cb9636b2-d9b3-466d-959c-14c7c8017a78
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erreur MSBuild MSB3254
**MSB3254 : Le fichier \<nom\> sera ignoré car il est illisible.  Le fichier a été passé dans InstalledAssemblySubsetTables ou a été trouvé lors de la recherche du dossier \<nom\> dans TargetFrameworkDirectories.**  
  
 Cette erreur se produit lorsque le fichier XML du [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)], client.xml, est illisible.  Le fichier est illisible car il a été altéré, endommagé ou verrouillé, ou bien à cause d'un autre problème.  
  
 Le [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] est un sous\-ensemble de la bibliothèque runtime [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 complète.  Pour plus d'informations sur le [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)], consultez [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
 Procédures  
  
### Pour corriger cette erreur  
  
-   Vérifiez que vous disposez des autorisations maximales et d'un accès complet au fichier ou réinstallez la bibliothèque runtime redistribuable du [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] pour remplacer le fichier endommagé.  
  
## Voir aussi  
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)