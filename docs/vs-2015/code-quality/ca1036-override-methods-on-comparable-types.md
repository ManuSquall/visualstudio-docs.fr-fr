---
title: 'CA1036 : Substituer les méthodes sur les types comparable | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1069316d0a027678b1161a948765bb81f1de68de
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202824"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036 : Substituer les méthodes sur les types Comparable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé implémente le <xref:System.IComparable?displayProperty=fullName> interface et ne se substitue pas <xref:System.Object.Equals%2A?displayProperty=fullName> ou ne pas surcharger l’opérateur spécifique à la langue pour l’égalité, inégalité, inférieur ou supérieur à. La règle ne signale pas d’une violation si le type hérite uniquement une implémentation de l’interface.

## <a name="rule-description"></a>Description de la règle
 Les types qui définissent un ordre de tri personnalisé implémentent la <xref:System.IComparable> interface. Le <xref:System.IComparable.CompareTo%2A> méthode retourne une valeur entière qui indique l’ordre de tri correct pour les deux instances du type. Cette règle identifie les types de définir un ordre de tri ; Cela implique que la signification ordinaire de l’égalité, inégalité, inférieure et supérieure ne s’appliquent pas. Lorsque vous fournissez une implémentation de <xref:System.IComparable>, vous devez généralement également substituer <xref:System.Object.Equals%2A> afin qu’il retourne des valeurs qui sont cohérents avec <xref:System.IComparable.CompareTo%2A>. Si vous substituez <xref:System.Object.Equals%2A> et codez dans un langage qui prend en charge les surcharges d’opérateur, vous devez également fournir des opérateurs sont cohérents avec <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, substituez <xref:System.Object.Equals%2A>. Si votre langage de programmation prend en charge la surcharge d’opérateur, fournissez les opérateurs suivants :

-   op_Equality

-   op_Inequality

-   op_LessThan

-   op_GreaterThan

 En c#, les jetons qui sont utilisés pour représenter ces opérateurs sont les suivantes : ==, ! =, \<, et >.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle lorsque la violation est provoquée par des opérateurs manquants et votre langage de programmation ne prend pas en charge la surcharge d’opérateur, comme c’est le cas avec Visual Basic .NET. Il est également possible de supprimer un avertissement de cette règle quand elle se déclenche sur les opérateurs d’égalité autres qu’op_Equality si vous déterminez que l’implémentation des opérateurs n’est pas pertinent dans votre contexte de l’application sans. Toutefois, vous ne devriez toujours op_Equality et l’opérateur == si vous se substitue à Object.Equals.

## <a name="example"></a>Exemple
 L’exemple suivant contient un type qui implémente correctement <xref:System.IComparable>. Commentaires de code identifient les méthodes qui satisfont différentes règles liées à <xref:System.Object.Equals%2A> et <xref:System.IComparable> interface.

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>Exemple
 L’application suivante teste le comportement de la <xref:System.IComparable> implémentation mentionnée précédemment.

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName>
 [Opérateurs d’égalité](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)



