---
title: "Erreur du compilateur CS1948 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1948"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1948"
ms.assetid: 3dac3abe-0edd-4ee1-8fb1-bc597ea63e1f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1948
La variable de portée 'name' ne peut pas avoir le même nom qu’un paramètre de type de méthode  
  
 Un même espace de déclaration ne peut pas contenir deux déclarations du même identificateur.  
  
### Pour corriger cette erreur  
  
1.  Modifiez le nom de la variable de portée ou du paramètre de type.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1948, car l’identificateur `T` est utilisé pour la variable de portée et pour le paramètre de type de la méthode `TestMethod` :  
  
```  
// cs1948.cs using System.Linq; class Test { public void TestMethod<T>(T t) { var x = from T in Enumerable.Range(1, 100) // CS1948 select T; } }  
```