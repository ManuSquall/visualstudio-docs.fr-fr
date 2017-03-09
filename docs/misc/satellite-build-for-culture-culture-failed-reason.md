---
title: "Satellite build for culture &#39;culture&#39; failed. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.satellite_build_failed"
ms.assetid: c97c589f-cf4d-4f6b-941a-7526a1091fce
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Satellite build for culture &#39;culture&#39; failed. &lt;reason&gt;
Un assembly satellite pour une culture donnée n'a pas pu être généré.  Cette erreur entraîne l'échec du processus de génération.  
  
 Cette erreur peut se produire pour deux raisons :  
  
1.  ALINK.EXE n'est pas installé sur le système.  
  
2.  ALINK.EXE a échoué mais n'a pas retourné d'informations d'erreurs étendues.  
  
 **Pour corriger cette erreur**  
  
-   Réinstallez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou juste le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
-   Lorsque \<raison\> mentionne que "L'utilitaire Assembly Linker n'a pas pu être lancé.  Le fichier existe", videz le dossier Temp dans lequel les fichiers sont générés \(par exemple, C:\\Documents et Paramètres \\\<utilisateur\>\\Local Settings\\Temp\).  
  
## Voir aussi  
 [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)