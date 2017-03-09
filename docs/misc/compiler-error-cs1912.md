---
title: "Erreur du compilateur CS1912 | Microsoft Docs"
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
  - "CS1912"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1912"
ms.assetid: 6205420e-01b9-4470-89f9-5924f1e49108
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1912
Initialisation du membre 'nom' en double  
  
 Un initialiseur d’objet ne peut initialiser chaque membre qu’une seule fois.  
  
### Pour corriger cette erreur  
  
1.  Supprimez la deuxième initialisation du membre dans l’initialiseur d’objet.  
  
## Exemple  
 Le code suivant génère l’erreur CS1912 car `memberA` est initialisé deux fois :  
  
```  
// cs1912.cs using System.Linq; public class TestClass { public int memberA { get; set; } public int memberB { get; set; } } public class Test { static void Main() { TestClass tc = new TestClass() { memberA = 5, memberA = 6, memberB = 2}; // CS1912 } }  
```  
  
## Voir aussi  
 [Initialiseurs d'objets et de collections](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)