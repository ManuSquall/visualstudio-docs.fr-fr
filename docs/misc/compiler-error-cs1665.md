---
title: "Erreur du compilateur CS1665 | Microsoft Docs"
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
  - "CS1665"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1665"
ms.assetid: 93d4a4af-23c3-4730-a778-77852e41db4d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1665
Les mémoires tampons de taille fixe doivent avoir une longueur supérieure à zéro  
  
 Cette erreur se produit si une mémoire tampon de taille fixe est déclaré avec une taille nulle ou négative. La longueur d’une mémoire tampon de taille fixe doit être un entier positif.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1665.  
  
```  
// CS1665.cs // compile with: /unsafe /target:library struct S { public unsafe fixed int A[0];   // CS1665 }  
```