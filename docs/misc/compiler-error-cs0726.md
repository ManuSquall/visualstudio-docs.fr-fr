---
title: "Erreur du compilateur CS0726 | Microsoft Docs"
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
  - "CS0726"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0726"
ms.assetid: 9ea5f004-cf25-4e6e-b9e5-6b53e4a7e1ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0726
'format specifier' n’est pas un spécificateur de format valide  
  
 Cette erreur se produit dans le débogueur. Quand vous tapez un nom de variable dans une fenêtre du débogueur, vous pouvez ajouter une virgule, puis un spécificateur de format à la suite du nom. Par exemple : `myInt, h` ou `myString,nq`. Cette erreur se produit quand le compilateur ne reconnaît pas le [Spécificateurs de format en C\#](../debugger/format-specifiers-in-csharp.md).