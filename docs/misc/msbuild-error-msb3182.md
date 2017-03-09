---
title: "MSBuild Error MSB3182 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.TargetPathTooLong"
helpviewer_keywords: 
  - "MSB3182"
ms.assetid: b257a206-b12b-453b-97d8-2cb9a0d3dcc9
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3182
**MSB3182 : Le nom de fichier '\<fichier\>' comprend plus de '\<longueur\>' caractères.**  
  
 Cet avertissement est généré lorsque la valeur de la propriété `TargetPath` est trop longue.  Il peut s'appliquer à la fois au manifeste d'application et de déploiement.  
  
### Pour corriger cette erreur  
  
-   Modifiez la valeur de la propriété `TargetPath` pour la raccourcir.  
  
## Voir aussi  
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)