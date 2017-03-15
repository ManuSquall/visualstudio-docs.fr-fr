---
title: "L’option /moduleassemblyname ne peut &#234;tre sp&#233;cifi&#233;e que lors de la g&#233;n&#233;ration d’une cible de type &#39;module&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc2030"
  - "vbc2030"
helpviewer_keywords: 
  - "BC2030"
ms.assetid: 2ebc577b-3464-40cc-8788-9fc9d3b4f928
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’option /moduleassemblyname ne peut &#234;tre sp&#233;cifi&#233;e que lors de la g&#233;n&#233;ration d’une cible de type &#39;module&#39;
L’option de compilateur `/moduleassemblyname` a été passée au compilateur Visual Basic alors que l’option `/target` a une valeur autre que `module`.  
  
 **ID d’erreur :** BC2030  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’option de compilateur `/moduleassemblyname` ou affectez à l’option `/target` la valeur `module`.  
  
## Voir aussi  
 [\/target](/dotnet/visual-basic/reference/command-line-compiler/target)   
 [\/moduleassemblyname](/dotnet/visual-basic/reference/command-line-compiler/moduleassemblyname)   
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)