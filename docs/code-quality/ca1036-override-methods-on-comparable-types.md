---
title: 'CA1036 : Substituer les méthodes sur les types comparable'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 05f4bd750f1ec2ad4d336acb1a00b8848de389bf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825579"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036 : Substituer les méthodes sur les types comparable

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé implémente le <xref:System.IComparable?displayProperty=fullName> interface et ne se substitue pas <xref:System.Object.Equals%2A?displayProperty=fullName> ou ne surcharge pas l’opérateur spécifique à la langue pour l’égalité, inégalité, moins-à ou supérieur-que. La règle ne signale pas d’une violation si le type hérite uniquement une implémentation de l’interface.

## <a name="rule-description"></a>Description de la règle

Les types qui définissent un ordre de tri personnalisé implémentent la <xref:System.IComparable> interface. Le <xref:System.IComparable.CompareTo%2A> méthode retourne une valeur entière qui indique l’ordre de tri correct pour les deux instances du type. Cette règle identifie les types de définir un ordre de tri. Définition d’un ordre de tri implique que la signification ordinaire d’égalité, inégalité, less- et inférieur-que ne s’appliquent pas. Lorsque vous fournissez une implémentation de <xref:System.IComparable>, vous devez généralement également substituer <xref:System.Object.Equals%2A> afin qu’il retourne des valeurs qui sont cohérents avec <xref:System.IComparable.CompareTo%2A>. Si vous substituez <xref:System.Object.Equals%2A> et codez dans un langage qui prend en charge les surcharges d’opérateur, vous devez également fournir des opérateurs sont cohérents avec <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, substituez <xref:System.Object.Equals%2A>. Si votre langage de programmation prend en charge la surcharge d’opérateur, fournissez les opérateurs suivants :

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

En c#, les jetons qui sont utilisés pour représenter ces opérateurs sont les suivantes :

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de règle CA1036 quand la violation est due à l’absence d’opérateurs et votre langage de programmation ne prend pas en charge la surcharge d’opérateur, comme c’est le cas avec Visual Basic. Il est également possible de supprimer un avertissement de cette règle quand elle se déclenche sur les opérateurs d’égalité autres qu’op_Equality si vous déterminez que l’implémentation des opérateurs n’est pas pertinent dans votre contexte de l’application sans. Toutefois, vous ne devriez toujours op_Equality et l’opérateur == si vous se substitue à Object.Equals.

## <a name="example"></a>Exemple
 L’exemple suivant contient un type qui implémente correctement <xref:System.IComparable>. Commentaires de code identifient les méthodes qui satisfont différentes règles liées à <xref:System.Object.Equals%2A> et <xref:System.IComparable> interface.

 [!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

## <a name="example"></a>Exemple
 L’application suivante teste le comportement de la <xref:System.IComparable> implémentation mentionnée précédemment.

 [!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>Voir aussi

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Opérateurs d’égalité](/dotnet/standard/design-guidelines/equality-operators)