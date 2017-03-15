---
title: "Erreur du compilateur CS0828 | Microsoft Docs"
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
  - "CS0828"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0828"
ms.assetid: e18ffe72-2fcc-436d-be7f-8c8365b86129
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0828
Impossible d’assigner 'expression' à une propriété de type anonyme  
  
 Un type anonyme ne peut pas être initialisé avec une valeur Null ou un type unsafe, ni avec un groupe de méthodes ou une fonction anonyme.  
  
### Pour corriger cette erreur  
  
1.  Ajoutez une déclaration de type à gauche de l’assignation, ou modifiez l’expression située à droite pour que son type soit acceptable.  
  
## Exemple  
 Le code suivant génère l’erreur CS0828, car un membre d’un type anonyme ne peut pas être initialisé avec une valeur Null.  
  
```  
// cs0828.cs using System; public class C { public static int Main() { var a = 1; var c = new { p1 = null }; // CS0828 return 1; } }  
```  
  
## Voir aussi  
 [Variables locales implicitement typées](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)