---
title: "Avertissement du compilateur (niveau&#160;1) CS1911 | Microsoft Docs"
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
  - "CS1911"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1911"
ms.assetid: 95e8a7a0-1c19-4930-a7e9-3ae4060e97d3
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS1911
L’accès au membre 'name' via un mot clé 'base' à partir d’une méthode anonyme, d’expression lambda, d’expression de requête ou d’un itérateur entraîne la génération d’un code non vérifiable. Si possible, déplacez l’accès vers une méthode d’assistance sur le type conteneur.  
  
 L’appel de fonctions virtuelles avec le mot clé `base` à l’intérieur du corps de méthode d’un itérateur ou de méthodes anonymes génère du code non vérifiable. Le code non vérifiable ne s’exécute pas dans un environnement de confiance partielle.  
  
 Pour résoudre l’erreur CS1911, une solution consiste à déplacer l’appel de fonction virtuelle vers une fonction d’assistance.  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS1911.  
  
```  
// CS1911.cs // compile with: /W:1 using System; delegate void D(); delegate D RetD(); class B { protected virtual void M() { Console.WriteLine("B.M"); } } class Der : B { protected override void M() { Console.WriteLine("D.M"); } void Test() { base.M(); } D Test2() { return new D(base.M); } public D CallBaseM() { return delegate () { base.M(); };   // CS1911 // try the following line instead // return delegate () { Test(); }; } public RetD DelToBaseM() { return delegate () { return new D(base.M); };   // CS1911 // try the following line instead // return delegate () { return Test2(); }; } } class Program { public static void Main() { Der der = new Der(); D d = der.CallBaseM(); d(); RetD rd = der.DelToBaseM(); rd()(); } }  
```