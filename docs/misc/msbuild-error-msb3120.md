---
title: "MSBuild Error MSB3120 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationExtensionTooLong"
helpviewer_keywords: 
  - "MSB3120"
ms.assetid: 20bc64f5-aadc-4eec-9915-a87a3d7f81ea
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3120
**MSB3120 : L'extension de l'association de fichier '\<extension\>' dépasse la longueur maximale autorisée de \<LongueurMaximale\>.**  
  
 Le nombre de caractères dans l'extension de l'association de fichier ne doit pas dépasser le nombre indiqué.  
  
### Pour corriger cette erreur  
  
-   Affectez à l'attribut `extension` de l'élément fileAssociation \(voir [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)\) une valeur qui ne contient pas plus de caractères que la limite autorisée pour le système d'exploitation cible.  
  
## Voir aussi  
 [Page Publier, Concepteur de projets](../ide/reference/publish-page-project-designer.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)