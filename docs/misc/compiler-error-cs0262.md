---
title: "Erreur du compilateur CS0262 | Microsoft Docs"
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
  - "CS0262"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0262"
ms.assetid: 44f8661f-c934-483f-84cd-00ca8257e50a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0262
Les déclarations partielles de 'type' ont des modificateurs d’accessibilité en conflit  
  
 Cette erreur se produit si un type partiel a des modificateurs incohérents tels que private, protected, internal ou abstract. Ces modificateurs doivent être cohérents dans toutes les déclarations partielles de ce type. Pour plus d'informations, consultez [Classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0262 :  
  
```  
// CS0262.cs class A { public partial class C  // CS0262 { } private partial class C { } }  
```