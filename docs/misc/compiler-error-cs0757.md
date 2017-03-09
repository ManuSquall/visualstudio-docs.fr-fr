---
title: "Erreur du compilateur CS0757 | Microsoft Docs"
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
  - "CS0757"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0757"
ms.assetid: ba093570-306d-4b7b-aad5-1a3855ad6776
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0757
Une méthode partielle ne peut pas avoir plusieurs déclarations d’implémentation  
  
 Une méthode partielle se compose exactement d’une déclaration de définition \(signature\) et d’une ou zéro déclaration d’implémentation \(corps\). Il n’est pas autorisé d’avoir plusieurs déclarations d’implémentation pour des déclarations de définition identiques. Les méthodes partielles peuvent être surchargées, et chaque version surchargée peut avoir une ou zéro déclaration d’implémentation.  
  
### Pour corriger cette erreur  
  
1.  Supprimez toutes les déclarations d’implémentation, sauf une, pour la méthode partielle.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0757 :  
  
```  
// cs0757.cs using System; public partial class C { // Defining declaration. partial void Part(); // Implementing declaration. partial void Part() { //...Do something. } // Second implementing declaration. partial void Part() // CS0757 { //...Do something. } public static int Main() { return 1; } }  
```  
  
## Voir aussi  
 [Classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)