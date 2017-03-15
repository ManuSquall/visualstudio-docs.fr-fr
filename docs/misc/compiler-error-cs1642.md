---
title: "Erreur du compilateur CS1642 | Microsoft Docs"
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
  - "CS1642"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1642"
ms.assetid: 2efeedf1-1839-485d-8b8c-9045df1951f0
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1642
Les champs de mémoire tampon de taille fixe ne peuvent être membres que de structs.  
  
 Cette erreur se produit si vous utilisez un champ de mémoire tampon de taille fixe dans `class` au lieu de `struct`. Pour résoudre cette erreur, remplacez  `class` par `struct` ou déclarez le champ comme un tableau ordinaire.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1642.  
  
```  
// CS1642.cs // compile with: /unsafe /target:library unsafe class C { fixed int a[10];   // CS1642 } unsafe struct D { fixed int a[10]; } unsafe class E { public int[] a = null; }  
```