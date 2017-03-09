---
title: "CA1036&#160;: Substituer les m&#233;thodes sur les types Comparable | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1036"
  - "OverrideMethodsOnComparableTypes"
helpviewer_keywords: 
  - "OverrideMethodsOnComparableTypes"
  - "CA1036"
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1036&#160;: Substituer les m&#233;thodes sur les types Comparable
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideMethodsOnComparableTypes|  
|CheckId|CA1036|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type public ou protégé implémente l'interface <xref:System.IComparable?displayProperty=fullName> et ne substitue pas <xref:System.Object.Equals%2A?displayProperty=fullName>, ni ne surcharge l'opérateur égal à, différent de, inférieur à ou supérieur à propre au langage.  La règle ne rapporte pas d'infraction si le type hérite seulement d'une implémentation de l'interface.  
  
## Description de la règle  
 Les types qui définissent un ordre de tri personnalisé implémentent l'interface <xref:System.IComparable>.  La méthode <xref:System.IComparable.CompareTo%2A> retourne une valeur entière qui indique l'ordre de tri approprié pour deux instances du type.  Cette règle identifie des types qui définissent un ordre de tri, en impliquant que la signification ordinaire des opérations égal à, différent de, supérieur à et inférieur à ne s'applique pas.  Lorsque vous fournissez une implémentation de <xref:System.IComparable>, vous devez généralement substituer aussi <xref:System.Object.Equals%2A> afin qu'il retourne des valeurs cohérentes avec <xref:System.IComparable.CompareTo%2A>.  Si vous substituez <xref:System.Object.Equals%2A> et codez dans un langage qui prend en charge les surcharges d'opérateur, vous devez également fournir des opérateurs cohérents avec <xref:System.Object.Equals%2A>.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, substituez <xref:System.Object.Equals%2A>.  Si votre langage de programmation prend en charge la surcharge d'opérateur, fournissez les opérateurs suivants :  
  
-   op\_Equality  
  
-   op\_Inequality  
  
-   op\_LessThan  
  
-   op\_GreaterThan  
  
 En C\#, les jetons utilisés pour représenter ces opérateurs sont les suivants : \=\=, \!\=, \<, et \>.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle lorsque la violation est provoquée par des opérateurs manquants et lorsque votre langage de programmation ne prend pas en charge la surcharge d'opérateur, comme c'est le cas avec Visual Basic .NET.  Par mesure de sécurité, il est également recommandé de supprimer un avertissement de cette règle quand elle se déclenche sur des opérateurs d'égalité autres que op\_Equality si vous considérez qu'il est inutile d'implémenter les opérateurs dans votre contexte d'application.  Cependant, vous devez toujours vérifier op\_Equality et l'opérateur \=\= si vous remplacez Object.Equals.  
  
## Exemple  
 L'exemple suivant contient un type qui implémente correctement <xref:System.IComparable>.  Les commentaires de code identifient les méthodes qui satisfont différentes règles en rapport avec <xref:System.Object.Equals%2A> et l'interface <xref:System.IComparable>.  
  
 [!code-cs[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]  
  
## Exemple  
 L'application suivante teste le comportement de l'implémentation <xref:System.IComparable> présentée précédemment.  
  
 [!code-cs[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]  
  
## Voir aussi  
 <xref:System.IComparable?displayProperty=fullName>   
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Opérateurs d'égalité](../Topic/Equality%20Operators.md)