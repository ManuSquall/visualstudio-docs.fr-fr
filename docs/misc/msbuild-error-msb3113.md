---
title: "MSBuild Error MSB3113 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.ResolveFailedInReadWriteMode"
helpviewer_keywords: 
  - "MSB3113"
ms.assetid: 81e73738-e6ee-4651-9f48-acb1feef3ff5
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3113
**MSB3113 : Impossible de trouver le fichier '\<fichier\>'.**  
  
 Cette erreur est générée lorsqu'une référence qui ne peut pas être résolue est détectée lors de la création d'un manifeste.  Elle peut provenir du fichier projet ou d'un paramètre de tâche.  
  
### Pour corriger cette erreur  
  
-   Vérifiez votre fichier projet \(et les paramètres de génération, si vous effectuez une génération personnalisée\) pour détecter tout conflit dans les références de fichier.  
  
## Voir aussi  
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)