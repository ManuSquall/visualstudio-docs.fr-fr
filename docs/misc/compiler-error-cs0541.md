---
title: "Erreur du compilateur CS0541 | Microsoft Docs"
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
  - "CS0541"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0541"
ms.assetid: ed812c07-24f7-43c6-9a44-553f27f6249d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0541
'declaration' : la déclaration d’interface explicite ne peut être déclarée que dans une classe ou une structure  
  
 Une déclaration d’[interface](/dotnet/csharp/language-reference/keywords/interface) explicite a été trouvée en dehors d’une [classe](/dotnet/csharp/language-reference/keywords/class) ou d’une [structure](/dotnet/csharp/language-reference/keywords/struct).  
  
 L’exemple suivant génère l’erreur CS0541 :  
  
```  
// CS0541.cs namespace x { interface IFace { void F(); } interface IFace2 : IFace { void IFace.F();   // CS0541 } }  
```