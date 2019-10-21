---
title: 'CA1036 : substituer les méthodes sur les types comparables | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 779e6258f9c5be256a7973a5d917045507fc82e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661826"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036 : Substituer les méthodes sur les types Comparable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé implémente l’interface <xref:System.IComparable?displayProperty=fullName> et ne remplace pas <xref:System.Object.Equals%2A?displayProperty=fullName> ou ne surcharge pas l’opérateur propre au langage pour l’égalité, l’inégalité, le signe inférieur à ou supérieur à. La règle ne signale pas de violation si le type hérite uniquement d’une implémentation de l’interface.

## <a name="rule-description"></a>Description de la règle
 Les types qui définissent un ordre de tri personnalisé implémentent l’interface <xref:System.IComparable>. La méthode <xref:System.IComparable.CompareTo%2A> retourne une valeur entière qui indique l’ordre de tri correct pour deux instances du type. Cette règle identifie les types qui définissent un ordre de tri ; Cela implique que la signification ordinaire de l’égalité, de l’inégalité, de inférieur à et supérieur à ne s’applique pas. Lorsque vous fournissez une implémentation de <xref:System.IComparable>, vous devez généralement remplacer <xref:System.Object.Equals%2A> afin qu’il retourne des valeurs qui sont cohérentes avec <xref:System.IComparable.CompareTo%2A>. Si vous substituez des <xref:System.Object.Equals%2A> et que vous écrivez du code dans un langage qui prend en charge les surcharges d’opérateur, vous devez également fournir des opérateurs qui sont cohérents avec <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, substituez <xref:System.Object.Equals%2A>. Si votre langage de programmation prend en charge la surcharge d’opérateur, fournissez les opérateurs suivants :

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

  Dans C#, les jetons utilisés pour représenter ces opérateurs sont les suivants : = =, ! =, \< et >.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle lorsque la violation est provoquée par des opérateurs manquants et que votre langage de programmation ne prend pas en charge la surcharge d’opérateur, comme c’est le cas avec Visual Basic .NET. Il est également possible de supprimer sans risque un avertissement pour à partir de cette règle lorsqu’il se déclenche sur des opérateurs d’égalité autres que op_Equality si vous déterminez que l’implémentation des opérateurs n’a pas de sens dans le contexte de votre application. Toutefois, vous devez toujours dépasser op_Equality et l’opérateur = = si vous remplacez Object. Equals.

## <a name="example"></a>Exemple
 L’exemple suivant contient un type qui implémente correctement <xref:System.IComparable>. Les commentaires de code identifient les méthodes qui répondent à différentes règles relatives à <xref:System.Object.Equals%2A> et à l’interface <xref:System.IComparable>.

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>Exemple
 L’application suivante teste le comportement de l’implémentation de <xref:System.IComparable> présentée précédemment.

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName>
 [Opérateurs d’égalité](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
