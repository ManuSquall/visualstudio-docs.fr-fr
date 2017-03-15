---
title: "MSBuild Error MSB3121 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationMissingAttribute"
helpviewer_keywords: 
  - "MSB3121"
ms.assetid: c1e83a2a-515f-412d-b8b7-4821e510a923
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3121
**MSB3121 : Il manque à l'élément d'association de fichiers du manifeste d'application un ou plusieurs des attributs requis suivants : extension, description, progID ou icône par défaut.**  
  
 L'élément fileAssociation \(voir [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)\) doit contenir des valeurs pour les quatre attributs.  
  
### Pour corriger cette erreur  
  
-   Affectez une valeur valide à chaque attribut de l'élément fileAssociation \(voir [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)\).  
  
## Voir aussi  
 [Page Publier, Concepteur de projets](../ide/reference/publish-page-project-designer.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)