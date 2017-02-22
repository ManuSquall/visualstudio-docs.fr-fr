---
title: "CA1010&#160;: Les collections doivent impl&#233;menter une interface g&#233;n&#233;rique | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1010"
  - "CollectionsShouldImplementGenericInterface"
helpviewer_keywords: 
  - "CA1010"
  - "CollectionsShouldImplementGenericInterface"
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# CA1010&#160;: Les collections doivent impl&#233;menter une interface g&#233;n&#233;rique
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CollectionsShouldImplementGenericInterface|  
|CheckId|CA1010|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type visible de l'extérieur implémente l'interface <xref:System.Collections.IEnumerable?displayProperty=fullName>, mais n'implémente pas l'interface <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>, et l'assembly conteneur cible [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  Cette règle ignore les types qui implémentent <xref:System.Collections.IDictionary?displayProperty=fullName>.  
  
## Description de la règle  
 Pour étendre la facilité d'utilisation d'une collection, implémentez l'une des interfaces de collection génériques.  La collection peut être ensuite utilisée pour remplir des types de collection génériques tels que :  
  
-   <xref:System.Collections.Generic.List%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, implémentez l'une des interfaces de collection génériques suivantes :  
  
-   <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.IList%601?displayProperty=fullName>  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle ; toutefois, l'utilisation de la collection sera plus limitée.  
  
## Exemple de violation  
  
### Description  
 L'exemple suivant présente une classe \(type référence\) qui dérive de la classe non générique `CollectionBase`, qui viole cette règle.  
  
### Code  
 [!code-cs[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]  
  
### Commentaires  
 Pour résoudre une violation de cette violation, vous devez implémenter les interfaces génériques ou modifier la classe de base en un type qui implémente déjà les interfaces génériques et les interfaces non génériques, telles que la classe `Collection<T>`.  
  
## Résoudre par modification de classe de base  
  
### Description  
 L'exemple suivant résout la violation en modifiant la classe de base non générique `CollectionBase` de la collection en classe générique `Collection<T>` \(`Collection(Of T)` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
### Code  
 [!code-cs[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]  
  
### Commentaires  
 Modifier la classe de base d'une classe déjà finale est considéré par les consommateurs existants comme une modification avec rupture.  
  
## Résoudre par implémentation d'interface  
  
### Description  
 L'exemple suivant résout la violation en implémentant ces interfaces génériques : `IEnumerable<T>`, `ICollection<T>` et `IList<T>` \(`IEnumerable(Of T)`, `ICollection(Of T)` et `IList(Of T)` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
### Code  
 [!code-cs[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]  
  
## Règles connexes  
 [CA1005 : Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1000 : Ne pas déclarer de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002 : Ne pas exposer de listes génériques](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003 : Utiliser les instances du gestionnaire d'événements génériques](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007 : Utiliser des classes génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Voir aussi  
 [Génériques](/dotnet/csharp/programming-guide/generics/index)