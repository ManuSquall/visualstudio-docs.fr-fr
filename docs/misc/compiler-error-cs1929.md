---
title: "Erreur du compilateur CS1929 | Microsoft Docs"
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
  - "CS1929"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1929"
ms.assetid: effdd5d4-e156-418b-9d45-4ca194ab4319
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1929
Argument d’instance : impossible de convertir 'typeA' en 'typeB'.  
  
 Cette erreur est générée quand vous tentez d’appeler une méthode d’extension à partir d’une classe qu’elle n’étend pas. Dans l’exemple suivant, la méthode d’extension est définie pour la classe dérivée `A`, mais pas pour la classe de base `B`.  
  
### Pour corriger cette erreur  
  
1.  Créez une méthode d’extension pour le type dans lequel vous devez l’appeler ou placez l’appel dans un objet du type étendu par la méthode existante.  
  
## Exemple  
 Le code suivant génère les erreurs CS1928 et CS1929 :  
  
```  
// cs1929.cs using System.Linq; using System.Collections; static class Ext { public static void ExtMethod(this A a) { } } class A : B { } class B { static void Main() { B b = new B(); b.ExtMethod(); // CS1929 } }  
```  
  
## Voir aussi  
 [Méthodes d'extension](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)