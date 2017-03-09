---
title: "Erreur du compilateur CS1510 | Microsoft Docs"
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
  - "CS1510"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1510"
ms.assetid: 3f5a69f1-7672-4194-a4ee-5753370fc736
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1510
Un argument ref ou out doit être une variable qui peut être assignée  
  
 Seule une variable peut être passée comme un paramètre [ref](/dotnet/csharp/language-reference/keywords/ref) dans un appel de méthode. Une valeur `ref` correspond au passage d’un pointeur.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1510 :  
  
```  
// CS1510.cs public class C { public static int j = 0; public static void M(ref int j) { j++; } public static void Main () { M (ref 2);   // CS1510, can't pass a number as a ref parameter // try the following to resolve the error // M (ref j); } }  
```