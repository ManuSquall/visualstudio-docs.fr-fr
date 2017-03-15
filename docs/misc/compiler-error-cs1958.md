---
title: "Erreur du compilateur CS1958 | Microsoft Docs"
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
  - "CS1958"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1958"
ms.assetid: bb6f3bb2-ea93-4d2e-984c-da9c99f5653f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1958
Les expressions d’initialiseur d’objet et de collection ne peuvent pas être appliquées à une expression de création de délégué  
  
 À la différence d’une classe ou d’un struct, un délégué n’a pas de membres. Un initialiseur d’objet n’a donc rien à initialiser. Si cette erreur se produit, il est fort possible que des accolades se trouvent après l’expression de création d’un délégué. Pour faire disparaître cette erreur, supprimez simplement les accolades.  
  
### Pour corriger cette erreur  
  
1.  Supprimez les accolades.  
  
## Exemple  
 Le code suivant génère l’erreur CS1958 :  
  
```  
// cs1958.cs public class MemberInitializerTest { delegate void D<T>(); public static void GenericMethod<T>() { } public static void Run() { D<int> genD = new D<int>(GenericMethod<int>) { }; // CS1958 // Try the following line instead // D<int> genD = new D<int>(GenericMethod<int>); } }  
```