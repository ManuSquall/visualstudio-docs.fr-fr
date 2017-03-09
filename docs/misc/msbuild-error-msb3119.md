---
title: "MSBuild Error MSB3119 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationExtensionMissingLeadDot"
helpviewer_keywords: 
  - "MSB3119"
ms.assetid: 52d68b0e-01d4-436f-a96c-733fd20a8c04
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3119
**MSB3119 : Les extensions des associations de fichiers doivent commencer par un point \(.\).**  
  
 Cette erreur se produit lorsque vous configurez une association de fichier et que l'extension ne commence pas par un point \(.\).  
  
### Pour corriger cette erreur  
  
-   Affectez à l'attribut `extension` de l'élément fileAssociation \(voir [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)\) une valeur qui commence par un point \(.\), par exemple, « .doc ».  
  
## Voir aussi  
 [Page Publier, Concepteur de projets](../ide/reference/publish-page-project-designer.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)