---
title: "Erreur du compilateur CS0514 | Microsoft Docs"
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
  - "CS0514"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0514"
ms.assetid: 74ce3010-f9e9-458c-8b68-cfb908a3e7a2
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0514
'constructor' : un constructeur statique ne peut pas avoir un appel de constructeur 'this' ou 'base' explicite  
  
 L’appel de `this` dans le constructeur statique n’est pas autorisé, car le constructeur statique est appelé automatiquement avant la création de toute instance de la classe. En outre, les constructeurs statiques ne sont pas hérités et ne peuvent pas être appelés directement.  
  
 Pour plus d’informations, consultez [this](/dotnet/csharp/language-reference/keywords/this) et [de base](/dotnet/csharp/language-reference/keywords/base).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0514 :  
  
```  
// CS0514.cs class A { static A() : base(0) // CS0514 { } public A(object o) { } } class B { static B() : this(null) // CS0514 { } public B(object o) { } }  
```