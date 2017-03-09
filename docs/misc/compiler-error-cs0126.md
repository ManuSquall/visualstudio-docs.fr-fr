---
title: "Erreur du compilateur CS0126 | Microsoft Docs"
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
  - "CS0126"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0126"
ms.assetid: 15fb0f38-ac9d-4c09-a69f-398a4903d790
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0126
Un objet d’un type convertible en 'type' est requis  
  
 Une instruction return est présente, mais elle ne retourne pas une valeur du type attendu. Pour plus d'informations, consultez [Propriétés](/dotnet/csharp/programming-guide/classes-and-structs/properties).  
  
 L’exemple suivant génère l’avertissement CS0126 :  
  
```  
// CS0126.cs public class a { public int i { set { } get { return;   // CS0126, specify a value to return } } }  
```