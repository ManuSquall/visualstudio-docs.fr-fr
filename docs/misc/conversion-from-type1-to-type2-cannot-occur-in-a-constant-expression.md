---
title: "Une conversion de &#39;&lt;type1&gt;&#39; en &#39;&lt;type2&gt;&#39; ne peut pas avoir lieu dans une expression constante | Microsoft Docs"
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
  - "bc30060"
  - "vbc30060"
helpviewer_keywords: 
  - "BC30060"
ms.assetid: bea60254-67b6-4881-91d2-47854c4d073c
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une conversion de &#39;&lt;type1&gt;&#39; en &#39;&lt;type2&gt;&#39; ne peut pas avoir lieu dans une expression constante
L’expression d’initialisation dans une instruction `Const` correspond à un type de données qui ne peut pas être convertie en type déclaré de la constante.  
  
 **ID d’erreur :** BC30060  
  
### Pour corriger cette erreur  
  
1.  Initialisez la constante avec une expression d’un type de données qui peut être converti en type déclaré pour la constante.  
  
## Voir aussi  
 [Const Statement](/dotnet/visual-basic/language-reference/statements/const-statement)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)