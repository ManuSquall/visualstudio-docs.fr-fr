---
title: "MSBuild Error MSB3181 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.DuplicateTargetPath"
helpviewer_keywords: 
  - "MSB3181"
ms.assetid: 49349fc2-3fa1-470d-a5cb-6ad72b93f408
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3181
**MSB3181 : Au moins deux fichiers ont le même chemin cible '\<CheminAccès\>'.**  
  
 Cet avertissement est généré pendant la génération du manifeste d'application lorsque au moins deux assemblys ou fichiers référencés partagent le même chemin d'accès cible.  Le chemin d'accès contient le nom de fichier et tous ces assemblys se remplacent mutuellement au moment du déploiement.  
  
## Voir aussi  
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)