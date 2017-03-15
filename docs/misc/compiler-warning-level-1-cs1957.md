---
title: "Avertissement du compilateur (niveau&#160;1) CS1957 | Microsoft Docs"
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
  - "CS1957"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1957"
ms.assetid: a4823211-52ce-4ffa-b19b-ee874069409f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS1957
Le membre 'nom' se substitue à 'méthode'. Il existe plusieurs candidats à la substitution au moment de l’exécution. La méthode appelée dépend de l’implémentation.  
  
 Les paramètres de méthode qui varient uniquement s’ils sont `ref` ou `out` ne peuvent pas être différenciés au moment de l’exécution.  
  
### Pour éviter cet avertissement  
  
1.  Attribuez un autre nom ou un nombre de paramètres différent à l’une des méthodes.  
  
## Exemple  
 Le code suivant génère l’erreur CS1957 :  
  
```  
// cs1957.cs class Base<T, S> { public virtual string Test(out T x) // CS1957 { x = default(T); return "Base.Test"; } public virtual void Test(ref S x) { } } class Derived : Base<int, int> { public override string Test(out int x) { x = 0; return "Derived.Test"; } static int Main() { int x; if (new Derived().Test(out x) == "Derived.Test") return 0; return 1; } }  
```