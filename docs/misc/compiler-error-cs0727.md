---
title: "Erreur du compilateur CS0727 | Microsoft Docs"
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
  - "CS0727"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0727"
ms.assetid: 54bfb87e-d759-4310-a8ab-02dccd06337c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0727
Spécificateur de format non valide  
  
 Cette erreur se produit dans le débogueur. Quand vous tapez un nom de variable dans une fenêtre du débogueur, vous pouvez ajouter une virgule, puis un spécificateur de format à la suite du nom. Exemples : myInt, h; ou myString, nq. Cette erreur se produit quand le compilateur est totalement incapable d’analyser ce que vous avez tapé. Pour résoudre cette erreur, retapez le nom de la variable en le faisant éventuellement suivre d’une virgule et d’un [spécificateur de format valide](../debugger/format-specifiers-in-csharp.md).