---
title: "Erreur du compilateur&#160;CS1918 | Microsoft Docs"
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
  - "CS1918"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1918"
ms.assetid: 9ad2cbbd-3c10-4d56-b4cd-385103d005d4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur&#160;CS1918
Les membres de la propriété 'name' de type 'type' ne peuvent pas être assignés avec un initialiseur d’objet car il s’agit d’un type valeur.  
  
 Cette erreur se produit quand vous essayez d’utiliser un initialiseur d’objet pour initialiser les propriétés d’un type struct qui est lui\-même une propriété de la classe en cours d’initialisation.  
  
### Pour corriger cette erreur  
  
1.  Si vous devez initialiser complètement les champs de la propriété dans l’initialiseur d’objet, remplacez le struct par un type de classe. Sinon, initialisez les membres du struct dans un appel de méthode distinct après avoir créé l’objet à l’aide de l’initialiseur d’objet.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1918 :  
  
```  
// cs1918.cs public struct MyStruct { public int i; } public class Test { private MyStruct str = new MyStruct(); public MyStruct Str { get { return str; } } public static int Main() { Test t = new Test { Str = { i = 1 } }; // CS1918 return 0; } }  
  
```  
  
## Voir aussi  
 [Initialiseurs d'objets et de collections](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)