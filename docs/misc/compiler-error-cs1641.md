---
title: "Erreur du compilateur CS1641 | Microsoft Docs"
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
  - "CS1641"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1641"
ms.assetid: ba6eab47-c28b-4531-b6a0-6d538b236d19
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1641
Un champ de mémoire tampon de taille fixe doit utiliser le spécificateur de la taille du tableau après le nom du champ  
  
 Contrairement aux tableaux normaux, les mémoires tampons de taille fixe exigent la spécification d’une taille constante au niveau du point de déclaration. Pour résoudre cette erreur, ajoutez un littéral entier positif ou un entier positif constant et placez les crochets après l’identificateur.  
  
 L’exemple suivant génère l’erreur CS1641 :  
  
```  
// CS1641.cs // compile with: /unsafe /target:library unsafe struct S { fixed int [] a;  // CS1641 // OK fixed int b [10]; const int c = 10; fixed int d [c]; }  
```