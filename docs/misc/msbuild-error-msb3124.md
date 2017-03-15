---
title: "MSBuild Error MSB3124 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsDuplicateExtensions"
helpviewer_keywords: 
  - "MSB3124"
ms.assetid: d8365103-aa9d-400e-9c24-0a43e2bfbd14
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3124
**MSB3124 : Une association de fichier a déjà été créée pour l'extension '\<NomExtension\>'.**  
  
 Cette erreur se produit lorsqu'une extension d'association de fichier en double est rencontrée.  
  
### Pour corriger cette erreur  
  
-   Supprimez les attributs `extension` de l'élément fileAssociation \(voir [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)\) qui ne sont pas uniques.  Chaque attribut d'extension de l'élément \<fileAssociation\> répertorié doit être unique.  
  
## Voir aussi  
 [Page Publier, Concepteur de projets](../ide/reference/publish-page-project-designer.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)