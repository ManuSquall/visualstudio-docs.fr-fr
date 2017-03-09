---
title: "&#39;&lt;nom_classe1&gt;&#39; ne peut pas h&#233;riter de &lt;type&gt; &#39;&lt;nom_classe2&gt;&#39;, car &#39;&lt;nom_classe2&gt;&#39; est d&#233;clar&#233; &#39;NotInheritable&#39; | Microsoft Docs"
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
  - "vbc30299"
  - "bc30299"
helpviewer_keywords: 
  - "BC30299"
ms.assetid: 627d50f5-9e75-495d-93f7-50096ba2ea08
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_classe1&gt;&#39; ne peut pas h&#233;riter de &lt;type&gt; &#39;&lt;nom_classe2&gt;&#39;, car &#39;&lt;nom_classe2&gt;&#39; est d&#233;clar&#233; &#39;NotInheritable&#39;
Une classe tente d’hériter d’une autre classe, mais la classe de base souhaitée est spécifiée comme `NotInheritable`. Les classes `NotInheritable` sont utilisées principalement pour empêcher toute dérivation accidentelle.  
  
 **ID d’erreur :** BC30299  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `NotInheritable` de la définition de la classe de base souhaitée, ou supprimez l’instruction `Inherits`.  
  
## Voir aussi  
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)   
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)