---
title: "Erreur du compilateur CS0759 | Microsoft Docs"
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
  - "CS0759"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0759"
ms.assetid: 96f0e178-adbf-4327-8934-ac282c428184
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0759
Aucune déclaration de définition trouvée pour la déclaration d’implémentation de la méthode partielle 'method'.  
  
 Une méthode partielle doit avoir une déclaration de définition qui définit la signature \(nom, type de retour et paramètres\) de la méthode. L’implémentation ou le corps de la méthode est facultatif.  
  
### Pour corriger cette erreur  
  
1.  Fournissez une déclaration de définition pour la méthode partielle dans l’autre partie d’une classe ou d’un struct partiel.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0759 :  
  
```  
// cs0759.cs using System; public partial class C { partial void Part() // CS0759 { } public static int Main() { return 1; } }  
```  
  
## Voir aussi  
 [Classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)