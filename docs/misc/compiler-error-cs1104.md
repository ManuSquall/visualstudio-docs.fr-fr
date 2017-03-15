---
title: "Erreur du compilateur&#160;CS1104 | Microsoft Docs"
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
  - "CS1104"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1104"
ms.assetid: 65bfe85f-8dd1-4aed-bcd1-1f7e0635868c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur&#160;CS1104
Un tableau de paramètres ne peut pas être utilisé avec le modificateur 'this' dans une méthode d’extension.  
  
 Le premier paramètre d’une méthode d’extension ne peut pas être un tableau params.  
  
### Pour corriger cette erreur  
  
1.  N’oubliez pas que le premier paramètre d’une définition de méthode d’extension spécifie le type que la méthode « étendra ». Il ne s’agit pas d’un paramètre d’entrée. La présence d’un tableau params à cet emplacement n’a donc aucun sens. Si vous devez passer un tableau params, définissez\-le en deuxième paramètre.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1104 :  
  
```  
// cs1104.cs // Compile with: /target:library public static class Extensions { public static void Test<T>(this params T[] tArr) {} // CS1104 }   
```  
  
## Voir aussi  
 [Méthodes d'extension](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [params](/dotnet/csharp/language-reference/keywords/params)