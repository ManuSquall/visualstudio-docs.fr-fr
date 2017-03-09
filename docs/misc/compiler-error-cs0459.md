---
title: "Erreur du compilateur CS0459 | Microsoft Docs"
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
  - "CS0459"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0459"
ms.assetid: 01b058dd-8d65-4e9d-9de1-d47f9488d22a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0459
Impossible de prendre l'adresse d'une variable locale en lecture seule  
  
 En langage C\#, trois scénarios communs génèrent des variables locales en lecture seule : `foreach`, `using` et `fixed`. Dans chacun de ces cas, vous n’êtes pas autorisé à écrire dans la variable locale en lecture seule ou à prendre son adresse. Cette erreur est générée lorsque le compilateur se rend compte que vous essayez de prendre l’adresse d’une variable locale en lecture seule.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0459 lorsqu’une tentative est effectuée pour prendre l’adresse d’une variable locale en lecture seule dans une boucle `foreach` et dans un bloc d’instructions`fixed`.  
  
```  
// CS0459.cs // compile with: /unsafe class A { public unsafe void M1() { int[] ints = new int[] { 1, 2, 3 }; foreach (int i in ints) { int *j = &i;  // CS0459 } fixed (int *i = &_i) { int **j = &i;  // CS0459 } } private int _i = 0; }  
```