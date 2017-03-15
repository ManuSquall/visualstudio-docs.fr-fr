---
title: "Erreur du compilateur CS1913 | Microsoft Docs"
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
  - "CS1913"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1913"
ms.assetid: 652494b3-9576-4a4c-a9ee-695f86c4a023
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1913
Impossible d’initialiser le membre 'name'. Il ne s’agit pas d’un champ ou d’une propriété.  
  
 Les initialiseurs d’objets ne peuvent être utilisés que pour initialiser les champs ou les propriétés accessibles.  
  
### Pour corriger cette erreur  
  
1.  Initialisez le membre de classe dans un constructeur normal ou une autre méthode d’initialisation.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1913 :  
  
```  
// cs1912.cs class A { public delegate void D(); public event D myEvent; } public class Test { static void Main() { A a = new A() {myEvent = M}; // CS1913 } public void M(){} }  
```  
  
## Voir aussi  
 [Classes et structs](/dotnet/csharp/programming-guide/classes-and-structs/index)