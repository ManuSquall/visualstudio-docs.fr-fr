---
title: "Erreur du compilateur CS0403 | Microsoft Docs"
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
  - "CS0403"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0403"
ms.assetid: 6e5d55ce-d6bf-419d-aded-aaa2e5963bb6
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0403
Impossible de convertir la valeur null en paramètre de type 'name' car il peut s’agir d’un type valeur non nullable. Envisagez d’utiliser plutôt default\('T'\).  
  
 Vous ne pouvez pas affecter null au type inconnu nommé car il peut s’agir d’un type valeur, qui n’autorise pas l’affectation de null. Si votre classe générique n’est pas destinée à accepter des types valeur, utilisez la contrainte de type classe. Si elle peut accepter des types valeur, comme les types intégrés, vous pouvez peut\-être remplacer l’affectation de null par l’expression `default(T)`, comme illustré dans l’exemple suivant.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0403 :  
  
```  
// CS0403.cs // compile with: /target:library class C<T> { public void f() { T t = null;  // CS0403 T t2 = default(T);   // OK } } class D<T> where T : class { public void f() { T t = null;  // OK } }  
```