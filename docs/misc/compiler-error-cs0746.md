---
title: "Erreur du compilateur CS0746 | Microsoft Docs"
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
  - "CS0746"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0746"
ms.assetid: 36baf7f2-b092-422c-ab53-95154bfceb0a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0746
Déclarateur de membre de type anonyme non valide. Les membres de type anonymes doivent être déclarés avec une assignation de membre, un nom simple ou un accès au membre.  
  
 Un type anonyme doit être déclaré avec une assignation de membre, un nom simple ou un accès au membre.  
  
### Pour corriger cette erreur  
  
1.  Assurez\-vous que votre déclaration utilise uniquement une assignation de membre, des noms simples ou des expressions d’accès au membre.  
  
## Exemple  
 Le code suivant génère l’erreur CS0746 dans la déclaration de `incorrect_1` et `incorrect_2`. Les déclarations suivantes montrent deux façons correctes de déclarer un type anonyme.  
  
```  
// cs0746.cs public class C { public static int Main() { int i = 100; string s = "Bottles of beer."; var incorrect_1 = new { a.b = 1 }; // CS0746 var incorrect_2 = new {100, "Bottles of beer."}; // CS0746 var correct_1 = new { i, s }; //OK var correct_2 = new {num = i, message = s}; // OK return 1; } }  
  
```  
  
## Voir aussi  
 [Types anonymes](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)