---
title: "Avertissement du compilateur (niveau&#160;4) CS0078 | Microsoft Docs"
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
  - "CS0078"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0078"
ms.assetid: 8d637be6-82bc-462c-bec5-217327bc8c40
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;4) CS0078
Le suffixe 'l' risque d'être facilement confondu avec le chiffre '1' \-\- utilisez plutôt 'L'  
  
 Le compilateur vous avertit lorsqu’il détecte un cast en long à l’aide d’un l minuscule au lieu d’un L majuscule.  
  
 L’exemple suivant génère l’avertissement CS0078 :  
  
```  
// CS0078.cs // compile with: /W:4 class test { public static void TestL(long i) { } public static void TestL(int i) { } public static void Main() { TestL(25l);   // CS0078 // try the following line instead // TestL(25L); } }  
```