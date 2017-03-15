---
title: "Erreur du compilateur CS0409 | Microsoft Docs"
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
  - "CS0409"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0409"
ms.assetid: 23d86c13-7978-41b7-a087-ffcea52476fa
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0409
Une clause de contrainte a déjà été spécifiée pour le paramètre de type 'paramètre\_type'. Toutes les contraintes pour un paramètre de type doivent être spécifiées dans une seule clause where.  
  
 Plusieurs clauses de contrainte \(clauses where\) ont été détectées pour un même paramètre de type. Supprimez les clauses where superflues ou corrigez les clauses where pour qu’il n’y ait qu’un seul paramètre de type dans chaque clause.  
  
```  
// CS0409.cs interface I { } class C<T1, T2> where T1 : I where T1 : I  // CS0409 – T1 used twice { }  
```