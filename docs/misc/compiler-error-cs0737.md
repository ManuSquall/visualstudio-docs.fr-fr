---
title: "Erreur du compilateur CS0737 | Microsoft Docs"
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
  - "CS0737"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0737"
ms.assetid: d2247770-5546-46f2-a01d-8e2ebfcbb859
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0737
'nom\_type' n’implémente pas le membre d’interface 'nom\_membre'. 'nom\_méthode' ne peut pas implémenter un membre d’interface, car il n’est pas public.  
  
 Les méthodes qui implémentent des membres d’interface doivent avoir une accessibilité 'public'. Tous les membres d’interface sont `public`.  
  
### Pour corriger cette erreur  
  
1.  Ajoutez le modificateur d’accès [public](/dotnet/csharp/language-reference/keywords/public) à la méthode.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0737 :  
  
```  
// cs0737.cs interface ITest { // Default access of private with no modifier. int Return42(); // Try the following line instead. // public int Return42(); } struct Struct1 : ITest // CS0737 { int Return42() { return (42); } } public class Test { public static int Main(string[] args) { Struct1 s1 = new Struct1(); return (1); } }  
```  
  
## Voir aussi  
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)