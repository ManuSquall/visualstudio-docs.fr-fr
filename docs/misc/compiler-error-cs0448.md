---
title: "Erreur du compilateur CS0448 | Microsoft Docs"
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
  - "CS0448"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0448"
ms.assetid: f577ab4c-1c8c-4a10-80a8-9ba9f66c3d25
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0448
Le type de retour pour l'opérateur \+\+ ou \-\- doit être le type conteneur ou dérivé du type conteneur  
  
 Lorsque vous remplacez les opérateurs `++` ou `--`, ils doivent retourner le même type que le type conteneur, ou retourner un type dérivé du type conteneur.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0448.  
  
```  
// CS0448.cs class C5 { public static int operator ++(C5 c) { return null; }   // CS0448 public static C5 operator --(C5 c) { return null; }   // OK public static void Main() {} }  
```  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0448.  
  
```  
// CS0448_b.cs public struct S { public static S? operator ++(S s) { return new S(); }   // CS0448 public static S? operator --(S s) { return new S(); }   // CS0448 } public struct T { // OK public static T operator --(T t) { return new T(); } public static T operator ++(T t) { return new T(); } public static T? operator --(T? t) { return new T(); } public static T? operator ++(T? t) { return new T(); } public static void Main() {} }  
```