---
title: "CA1036 : Substituer les méthodes sur les types comparable | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d07e63363542a9bf5a1dd756026183349659abe1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036 : Substituer les méthodes sur les types Comparable
|||  
|-|-|  
|TypeName|OverrideMethodsOnComparableTypes|  
|CheckId|CA1036|  
|Catégorie|Microsoft.Design|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type public ou protégé implémente les <xref:System.IComparable?displayProperty=fullName> de l’interface et ne remplace pas <xref:System.Object.Equals%2A?displayProperty=fullName> ou ne surcharge pas l’opérateur spécifique à la langue pour l’égalité, inégalité, inférieur ou supérieur. La règle ne signale pas d’une violation si le type hérite seulement d’une implémentation de l’interface.  
  
## <a name="rule-description"></a>Description de la règle  
 Les types qui définissent un ordre de tri personnalisé implémentent la <xref:System.IComparable> interface. Le <xref:System.IComparable.CompareTo%2A> méthode retourne un entier qui indique l’ordre de tri correct pour les deux instances du type. Cette règle identifie les types de définir un ordre de tri ; Cela implique que la signification ordinaire de l’égalité, inégalité, inférieure et supérieure ne s’appliquent pas. Lorsque vous fournissez une implémentation de <xref:System.IComparable>, vous devez généralement également substituer <xref:System.Object.Equals%2A> afin qu’elle retourne des valeurs qui sont cohérents avec <xref:System.IComparable.CompareTo%2A>. Si vous substituez <xref:System.Object.Equals%2A> et codez dans un langage qui prend en charge les surcharges d’opérateur, vous devez également fournir des opérateurs cohérents avec <xref:System.Object.Equals%2A>.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, substituez <xref:System.Object.Equals%2A>. Si votre langage de programmation prend en charge la surcharge d’opérateur, fournissez les opérateurs suivants :  
  
-   op_Equality  
  
-   op_Inequality  
  
-   op_LessThan  
  
-   op_GreaterThan  
  
 Dans c#, les jetons sont utilisés pour représenter ces opérateurs sont les suivants : ==, ! =, \<, et >.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle lorsque la violation est provoquée par des opérateurs manquants et votre langage de programmation ne prend pas en charge la surcharge d’opérateur, comme c’est le cas avec Visual Basic .NET. Il est également possible de supprimer un avertissement de cette règle quand elle se déclenche sur les opérateurs d’égalité autres qu’op_Equality si vous déterminez qu’implémente les opérateurs ne se justifie pas dans le contexte de votre application sans. Toutefois, vous ne devriez toujours op_Equality et l’opérateur == si vous substituez Object.Equals.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant contient un type qui implémente correctement <xref:System.IComparable>. Commentaires de code identifient les méthodes qui satisfont différentes règles liées à <xref:System.Object.Equals%2A> et <xref:System.IComparable> interface.  
  
 [!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’application suivante teste le comportement de la <xref:System.IComparable> implémentation a été indiquée précédemment.  
  
 [!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IComparable?displayProperty=fullName>   
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Opérateurs d’égalité](/dotnet/standard/design-guidelines/equality-operators)