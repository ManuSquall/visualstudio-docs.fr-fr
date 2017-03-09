---
title: "MSBuild Error MSB3188 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.PrerequisiteNotSigned"
helpviewer_keywords: 
  - "MSB3188"
ms.assetid: 8520e960-3b31-4e25-9fce-b9092b869bd0
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3188
**MSB3188 : L'assembly '\<assembly\>' doit être signé avec une signature forte pour être marqué comme composant requis.**  
  
 Cette erreur est générée lorsqu'un assembly requis n'est pas signé avec une signature forte.  Elle s'applique uniquement aux manifestes d'application.  
  
### Pour corriger cette erreur  
  
-   Vérifiez que tous les assemblys utilisés par le projet sont signés avec une signature forte.