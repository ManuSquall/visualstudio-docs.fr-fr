---
title: "Les types d&#233;clar&#233;s &#39;Private&#39; doivent se trouver &#224; l’int&#233;rieur d’un autre type | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31089"
  - "bc31089"
helpviewer_keywords: 
  - "BC31089"
ms.assetid: 44ea5fe4-4af6-4cea-a4a5-2cf966df2937
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les types d&#233;clar&#233;s &#39;Private&#39; doivent se trouver &#224; l’int&#233;rieur d’un autre type
Le modificateur `Private` a été utilisé sur un type qui ne se trouve pas dans un autre type.  
  
 **ID d’erreur :** BC31089  
  
### Pour corriger cette erreur  
  
1.  Utilisez un modificateur d’accès moins restrictif, tel que `Friend`.  
  
2.  Déclarez le type dans un autre type.  
  
## Voir aussi  
 [Private](/dotnet/visual-basic/language-reference/modifiers/private)