---
title: "MSBuild Error MSB3186 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.NoIdentity"
helpviewer_keywords: 
  - "MSB3186"
ms.assetid: 1219fef4-9114-401c-875b-1dc69697fd9f
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3186
**MSB3186 : Impossible de déduire l'identité de l'assembly d'après les paramètres d'entrée de la tâche définis pour le manifeste généré.**  
  
 Cette erreur est générée lorsque le processus de génération ne peut pas déduire le nom d'un assembly pour le manifeste d'application ou de déploiement.  Le nom de l'assembly n'est pas attribué explicitement ; aucune identité n'est définie dans le manifeste de base, et l'identité du point d'entrée n'est pas spécifiée également.  
  
## Voir aussi  
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)