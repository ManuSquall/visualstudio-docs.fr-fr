---
title: "Erreur du compilateur CS1666 | Microsoft Docs"
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
  - "CS1666"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1666"
ms.assetid: 4d62aa9c-71b9-4c6e-8141-2426d20ac243
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1666
Vous ne pouvez pas utiliser des mémoires tampons de taille fixe contenues dans des expressions non fixed. Essayez d’utiliser l’instruction fixed.  
  
 Cette erreur se produit quand vous utilisez une mémoire tampon de taille fixe dans une expression impliquant une classe non fixed. Le runtime est libre de déplacer la classe non fixed pour optimiser l’accès à la mémoire, ce qui peut entraîner des erreurs quand vous utilisez de la mémoire tampon de taille fixe. Pour éviter cette erreur, utilisez le mot clé `fixed` dans l’instruction.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1666.  
  
```  
// CS1666.cs // compile with: /unsafe /target:library unsafe struct S { public fixed int buffer[1]; } unsafe class Test { S field = new S(); private bool example1() { return (field.buffer[0] == 0);   // CS1666 error } private bool example2() { // OK fixed (S* p = &field) { return (p->buffer[0] == 0); } } private bool example3() { S local = new S(); return (local.buffer[0] == 0); } }  
```