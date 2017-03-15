---
title: "Erreur du compilateur CS0261 | Microsoft Docs"
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
  - "CS0261"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0261"
ms.assetid: c2af7b31-4a48-457a-8d9b-0956dd0d46f9
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0261
Les déclarations partielles de 'type' ne doivent être que des classes, des structs ou des interfaces  
  
 Cette erreur se produit si un type partiel est déclaré comme un type de construction différent à divers emplacements. Pour plus d'informations, consultez [Classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
 L’exemple suivant génère l’erreur CS0261 :  
  
```  
// CS0261.cs partial class A  // CS0261 – A declared as a class here, but as a struct below { } partial struct A { }  
```