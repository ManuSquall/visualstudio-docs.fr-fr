---
title: "Erreur du compilateur CS0196 | Microsoft Docs"
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
  - "CS0196"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0196"
ms.assetid: d361484e-73b8-439a-99c7-714e61d73755
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0196
Un pointeur ne doit être indexé que par une seule valeur  
  
 Un pointeur ne peut pas avoir plusieurs index. Pour plus d'informations, consultez [Types pointeur](/dotnet/csharp/programming-guide/unsafe-code-pointers/pointer-types)  
  
 L’exemple suivant génère l’erreur CS0196 :  
  
```  
// CS0196.cs public class MyClass { public static void Main () { int *i = null; int j = 0; j = i[1,2];   // CS0196 // try the following line instead // j = i[1]; } }  
```