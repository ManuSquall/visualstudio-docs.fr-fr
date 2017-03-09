---
title: "Erreur du compilateur CS1100 | Microsoft Docs"
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
  - "CS1100"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1100"
ms.assetid: ea233371-36b6-49ae-a98c-a00ee3b79e53
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1100
La méthode 'nom' a un modificateur de paramètre 'this' qui ne se trouve pas sur le premier paramètre  
  
 Le modificateur `this` n’est autorisé qu’au niveau du premier paramètre d’une méthode, ce qui indique au compilateur que la méthode est une méthode d’extension.  
  
### Pour corriger cette erreur  
  
1.  Supprimez le modificateur `this` partout sauf au niveau du premier paramètre de la méthode.  
  
## Exemple  
 Le code suivant génère l’erreur CS1100, car un paramètre `this`  modifie le deuxième paramètre :  
  
```  
// cs1100.cs static class Test { static void ExtMethod(int i, this Test c) // CS1100 { } }  
```  
  
## Voir aussi  
 [Méthodes d'extension](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)