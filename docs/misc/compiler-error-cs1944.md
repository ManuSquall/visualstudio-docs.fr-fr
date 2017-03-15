---
title: "Erreur du compilateur CS1944 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1944"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1944"
ms.assetid: e5e2c018-9a7e-48ee-8dd3-98e3553777c1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1944
Une arborescence de l'expression ne peut pas contenir une opération pointeur unsafe  
  
 Les arborescences d’expression ne prennent pas en charge les types pointeur, car la méthode <xref:System.Linq.Expressions.Expression%601.Compile%2A?displayProperty=fullName> est uniquement autorisée à produire du code vérifiable. Consultez les commentaires.  
  
### Pour corriger cette erreur  
  
1.  N’utilisez pas de types pointeur au moment de créer une arborescence d’expression.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1944 :  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Dans certains cas, il est possible d’utiliser des pointeurs dans les arborescences d’expression. Considérons par exemple le code suivant :  
  
 `Expression<Func\<int*[], int*[]>) e = (int*[] i)=>i;`  
  
 Ce code est une arborescence d’expression valide, car aucun argument de type n’est un type pointeur. Ce sont des tableaux de pointeurs et les tableaux ne sont pas des types pointeur. De même, le corps de l’arborescence d’expression ne fait rien de risqué avec quelque pointeur que ce soit.  
  
## Voir aussi  
 [unsafe](/dotnet/csharp/language-reference/keywords/unsafe)