---
title: "&#39;MustOverride&#39; ne peut pas &#234;tre sp&#233;cifi&#233; sur &#39;&lt;nom_proc&#233;dure&gt;&#39;, car il est dans un type partiel d&#233;clar&#233; &#39;NotInheritable&#39; dans une autre d&#233;finition partielle. | Microsoft Docs"
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
  - "vbc30927"
  - "BC30927"
helpviewer_keywords: 
  - "BC30927"
ms.assetid: 5798dfda-3d7b-4f30-9715-40cbf52d6dc4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;MustOverride&#39; ne peut pas &#234;tre sp&#233;cifi&#233; sur &#39;&lt;nom_proc&#233;dure&gt;&#39;, car il est dans un type partiel d&#233;clar&#233; &#39;NotInheritable&#39; dans une autre d&#233;finition partielle.
Une procédure ou une propriété est déclarée comme `MustOverride` dans une classe définie dans plusieurs déclarations partielles, mais l’une des définitions partielles spécifie `NotInheritable` pour la classe.  
  
 Quand vous divisez la définition d’une classe en plusieurs déclarations partielles, le compilateur traite la classe comme l’union de toutes ses déclarations partielles. Cela s’applique non seulement aux membres, mais aussi à l’implémentation, à l’héritage et au niveau d’accès.  
  
 Pour substituer une procédure ou une propriété, une classe doit en hériter d’une classe de base. Par conséquent, vous devez spécifier `MustInherit` pour la classe afin de spécifier `MustOverride` pour une procédure ou une propriété dans une classe de base. Ces mots clés étant mutuellement contradictoires, vous ne pouvez pas spécifier `MustInherit` et `NotInheritable` pour la même classe.  
  
 **ID d’erreur :** BC30927  
  
### Pour corriger cette erreur  
  
-   Si la propriété ou la procédure doit être substituée, supprimez le mot clé `NotInheritable` de la déclaration partielle dans laquelle il apparaît.  
  
-   Si la classe doit avoir la valeur `NotInheritable`, supprimez le mot clé `MustOverride` de la procédure ou la propriété. Vous ne pouvez pas le substituer, car vous ne pouvez pas hériter de la classe.  
  
## Voir aussi  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)