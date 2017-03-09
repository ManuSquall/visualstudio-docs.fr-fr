---
title: "Erreur du compilateur CS0736 | Microsoft Docs"
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
  - "CS0736"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0736"
ms.assetid: 06b14feb-81d5-495f-ab2d-6dc3f5e7216f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0736
'type name' n’implémente pas le membre d’interface 'member name'. 'method name' ne peut pas implémenter un membre d’interface, car elle est statique.  
  
 Cette erreur est générée quand une méthode statique est implicitement ou explicitement déclarée en tant qu’implémentation d’un membre d’interface.  
  
### Pour corriger cette erreur  
  
-   Supprimez le modificateur [static](/dotnet/csharp/language-reference/keywords/static) de la déclaration de méthode.  
  
-   Modifiez le nom de la méthode d’interface.  
  
-   Redéfinissez le type conteneur pour qu’il n’hérite pas de l’interface.  
  
## Exemple  
 Le code suivant génère l’erreur CS0736, car `Program.testMethod` est déclaré statique :  
  
```  
// cs0736.cs namespace CS0736 { interface ITest { int testMethod(int x); } class Program : ITest // CS0736 { public static int testMethod(int x) { return 0; } // Try the following line instead. // public int testMethod(int x) { return 0; } public static void Main() { } } }  
```  
  
## Voir aussi  
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)