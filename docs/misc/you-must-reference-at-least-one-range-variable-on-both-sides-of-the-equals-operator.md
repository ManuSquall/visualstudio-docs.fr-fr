---
title: "Vous devez r&#233;f&#233;rencer au moins une variable de port&#233;e des deux c&#244;t&#233;s de l’op&#233;rateur &#39;Equals&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36622"
  - "bc36622"
helpviewer_keywords: 
  - "BC36622"
ms.assetid: 8d301227-131d-4977-b3ff-1fc4e427f8fa
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vous devez r&#233;f&#233;rencer au moins une variable de port&#233;e des deux c&#244;t&#233;s de l’op&#233;rateur &#39;Equals&#39;
Vous devez référencer au moins une variable de portée des deux côtés de l’opérateur 'Equals'. La ou les variables de portée \<variable\(s\)\> doivent apparaître d’un côté de l’opérateur 'Equals' alors que la ou les variables de portée \<variable\(s\)\> doivent apparaître de l’autre côté.  
  
 Les variables de portée identifiées pour des collections à joindre dans une requête LINQ doivent se trouver aux côtés opposés de l’opérateur `Equals`, en fonction de la collection pour laquelle ils sont identifiés. Autrement dit, les variables de plage identifiées pour l’une des collections jointes doivent se trouver du côté opposé de l’opérateur `Equals` par rapport aux variables de plage de l’autre collection jointe. Vous ne pouvez pas mélanger des variables de portée de collections différentes du même côté de l’opérateur `Equals`.  
  
 Au moins une variable de chaque collection jointe doit être référencée de chaque côté de l’opérateur `Equals`.  
  
 **ID d’erreur :** BC36622  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)   
 [Join Clause](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Group Join Clause](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [From Clause](/dotnet/visual-basic/language-reference/queries/from-clause)   
 [Select Clause](/dotnet/visual-basic/language-reference/queries/select-clause)