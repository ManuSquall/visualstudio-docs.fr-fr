---
title: "Erreur du compilateur CS0764 | Microsoft Docs"
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
  - "CS0764"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0764"
ms.assetid: 76a64149-49d8-40ea-a976-03835d8fb7eb
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0764
Soit les deux déclarations de méthode partielles sont unsafe, soit aucune ne l’est  
  
 Une méthode partielle se compose d’une déclaration de définition \(signature\) et d’une déclaration d’implémentation facultative \(corps\). Si la déclaration de définition a le modificateur `unsafe`, la déclaration d’implémentation doit également l’avoir. À l’inverse, si la déclaration d’implémentation a le modificateur `unsafe`, la déclaration de définition doit également l’avoir.  
  
### Pour corriger cette erreur  
  
1.  En supposant que la déclaration de définition est correcte, ajoutez ou supprimez le modificateur `unsafe` de la déclaration d’implémentation pour correspondre à la déclaration de définition.  
  
## Exemple  
  
```  
// cs0764.cs //  Compile with: /target:library /unsafe public partial class C { partial void Part(); unsafe partial void Part() //CS0764 { } public static int Main() { return 1; } }  
```  
  
## Voir aussi  
 [Classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)