---
title: "Erreur du compilateur CS0522 | Microsoft Docs"
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
  - "CS0522"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0522"
ms.assetid: f749f21e-92ee-495c-9b53-179ce9342d05
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0522
'constructeur' : les structures ne peuvent pas appeler les constructeurs de classe de base  
  
 Un [struct](/dotnet/csharp/language-reference/keywords/struct) ne peut pas appeler un constructeur de classe de base. Supprimez l’appel au constructeur de classe de base.  
  
 L’exemple suivant génère l’erreur CS0522 :  
  
```  
// CS0522.cs public class clx { public clx(int i) { } public static void Main() { } } public struct cly { public cly(int i):base(0)   // CS0522 // try the following line instead // public cly(int i) { } }  
```