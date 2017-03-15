---
title: "Avertissement du compilateur (niveau&#160;3) CS0419 | Microsoft Docs"
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
  - "CS0419"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0419"
ms.assetid: de439ad5-422f-4ed6-96d6-69dade29c7b2
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;3) CS0419
Référence ambiguë dans l’attribut cref : 'nom\_méthode1'.  'nom\_méthode2', pris par défaut, mais peut aussi correspondre à d’autres surcharges, notamment 'nom\_méthode'.  
  
 Dans un commentaire de documentation XML du code, une référence n’a pas pu être résolue. Cela peut se produire si la méthode est surchargée ou si deux identificateurs portent le même nom. Pour résoudre l’avertissement, utilisez un nom qualifié pour désambiguïser la référence ou mettez la surcharge spécifique entre parenthèses.  
  
 L’exemple suivant génère l’erreur CS0419 :  
  
```  
// cs0419.cs // compile with: /doc:x.xml /W:3 interface I { /// text for F(void) void F(); /// text for F(int) void F(int i); } /// text for class MyClass public class MyClass { /// <see cref="I.F"/> public static void MyMethod(int i) { } /* Try this instead: /// <see cref="I.F(int)"/> public static void MyMethod(int i) { } */ /// text for Main public static void Main () { } }  
```