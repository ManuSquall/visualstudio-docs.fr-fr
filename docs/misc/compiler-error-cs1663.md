---
title: "Erreur du compilateur CS1663 | Microsoft Docs"
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
  - "CS1663"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1663"
ms.assetid: 013f36ac-8925-4cee-9008-54fa7ad1324b
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1663
Le type de mémoire tampon de taille fixe doit être : bool, byte, short, int, long, char, sbyte, ushort, uint, ulong, float ou double  
  
 Une mémoire tampon de taille fixe ne peut pas être d’un type autre que ceux répertoriés. Pour éviter cette erreur, utilisez un autre type ou n’utilisez pas un tableau fixe.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1663.  
  
```  
// CS1663.cs // compile with: /unsafe /target:library unsafe struct C { fixed string ab[10];   // CS1663 }  
```