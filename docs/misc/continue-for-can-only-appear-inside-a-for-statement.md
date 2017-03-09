---
title: "&#39;Continue For&#39; ne peut &#234;tre utilis&#233; qu’&#224; l’int&#233;rieur d’une instruction &#39;For&#39; | Microsoft Docs"
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
  - "bc30783"
  - "vbc30783"
helpviewer_keywords: 
  - "BC30783"
ms.assetid: 70891018-27c8-4d36-b168-8cc7177d70cb
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Continue For&#39; ne peut &#234;tre utilis&#233; qu’&#224; l’int&#233;rieur d’une instruction &#39;For&#39;
Une instruction `Continue For` ne peut figurer qu’à l’intérieur d’une boucle `For...Next`.  
  
 **ID d’erreur :** BC30783  
  
### Pour corriger cette erreur  
  
1.  Si l’instruction `Continue For` se trouve dans un `Do...Loop`, remplacez l’instruction par `Continue Do`.  
  
     \- ou \-  
  
     Si l’instruction `Continue For` se trouve dans une boucle `While...End While`, remplacez l’instruction par `Continue While`.  
  
2.  Sinon, supprimez l’instruction `Continue For`.  
  
## Voir aussi  
 [Continue Statement](/dotnet/visual-basic/language-reference/statements/continue-statement)   
 [For...Next, instruction](/dotnet/visual-basic/language-reference/statements/for-next-statement)