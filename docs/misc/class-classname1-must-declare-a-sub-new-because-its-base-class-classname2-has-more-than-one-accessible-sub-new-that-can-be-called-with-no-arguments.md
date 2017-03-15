---
title: "La classe &#39;&lt;nom_classe1&gt;&#39; doit d&#233;clarer un &#39;Sub New&#39;, car sa classe de base &#39;&lt;nom_classe2&gt;&#39; comporte plusieurs &#39;Sub New&#39; accessibles pouvant &#234;tre appel&#233;s sans arguments | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32036"
  - "vbc32036"
helpviewer_keywords: 
  - "BC32036"
ms.assetid: 9b96387e-337e-4b2a-b49f-783c7e13811a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La classe &#39;&lt;nom_classe1&gt;&#39; doit d&#233;clarer un &#39;Sub New&#39;, car sa classe de base &#39;&lt;nom_classe2&gt;&#39; comporte plusieurs &#39;Sub New&#39; accessibles pouvant &#234;tre appel&#233;s sans arguments
Une classe dérivée ne déclare pas de constructeur et [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ne peut pas en générer un car il ne peut pas déterminer le constructeur de classe de base à appeler.  
  
 Quand une classe dérivée ne déclare pas de constructeur, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] tente de générer un constructeur sans paramètre implicite qui appelle `MyBase.New()`. S’il n’existe aucun constructeur accessible dans la classe de base pouvant être appelé sans arguments, ou s’il en existe plusieurs, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ne peut pas générer de constructeur implicite.  
  
 Cette situation peut survenir, par exemple, si un constructeur de classe de base comporte un seul argument `Optional` et qu’un autre constructeur comporte un seul argument `ParamArray`. Chacun d’eux peut être appelé sans argument.  
  
 **ID d’erreur :** BC32036  
  
### Pour corriger cette erreur  
  
1.  Déclarez et implémentez au moins un constructeur `Sub New` dans la classe dérivée.  
  
2.  Ajoutez un appel à un constructeur de classe de base, `MyBase.New()`, en tant que première ligne de chaque `Sub New`.  
  
## Voir aussi  
 [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [NOT IN BUILD : Utilisation des constructeurs et des destructeurs](http://msdn.microsoft.com/fr-fr/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [Optional](/dotnet/visual-basic/language-reference/modifiers/optional)   
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [Optional Parameters](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)   
 [Parameter Arrays](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)