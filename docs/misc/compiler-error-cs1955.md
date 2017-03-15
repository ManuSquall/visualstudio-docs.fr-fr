---
title: "Erreur du compilateur CS1955 | Microsoft Docs"
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
  - "CS1955"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1955"
ms.assetid: 38a8542d-da53-4739-b807-46c8c077363c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1955
Impossible d’utiliser un membre 'name' ne pouvant pas être appelé comme une méthode.  
  
 Seuls les méthodes et les délégués peuvent être appelés. Cette erreur est générée quand vous essayez d’utiliser des parenthèses vides pour appeler autre chose qu’une méthode ou un délégué.  
  
### Pour corriger cette erreur  
  
1.  Supprimez les parenthèses de l’expression.  
  
## Exemple  
 Le code suivant génère l’erreur CS1955 car le code essaie d’appeler un champ et une propriété à l’aide de l’opérateur d’appel de méthode [\(\)](/dotnet/csharp/language-reference/operators/invocation-operator). Vous ne pouvez pas appeler un champ ou une propriété, mais vous pouvez accéder à la valeur qu’il ou elle stocke à l’aide de l’opérateur d’accès au membre \([.](/dotnet/csharp/language-reference/operators/member-access-operator)\).  
  
```  
// cs1955.cs class A { public int x = 0; public int X { get { return x; } set { x = value; } } } class Test { static int Main() { A a = new A(); a.x(); // CS1955 a.X(); // CS1955 // Try this line instead: // int num = a.x; } }  
```