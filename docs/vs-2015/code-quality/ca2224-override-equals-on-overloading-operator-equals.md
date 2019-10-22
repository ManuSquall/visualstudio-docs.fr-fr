---
title: 'CA2224 : la substitution est égale à l’opérateur de surcharge égal à | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d35052bb2a1efb1a466ffc67c95c83e5b3a76533
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671879"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224 : Remplacez Equals au moment de surcharger l'opérateur égal
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type public implémente l’opérateur d’égalité, mais ne remplace pas <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 L’opérateur d’égalité est destiné à être un moyen syntaxiquement pratique d’accéder aux fonctionnalités de la méthode <xref:System.Object.Equals%2A>. Si vous implémentez l’opérateur d’égalité, sa logique doit être identique à celle de <xref:System.Object.Equals%2A>.

 Le C# compilateur émet un avertissement si votre code enfreint cette règle.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, vous devez supprimer l’implémentation de l’opérateur d’égalité ou substituer <xref:System.Object.Equals%2A> et faire en sorte que les deux méthodes retournent les mêmes valeurs. Si l’opérateur d’égalité n’introduit pas de comportement incohérent, vous pouvez corriger la violation en fournissant une implémentation de <xref:System.Object.Equals%2A> qui appelle la méthode <xref:System.Object.Equals%2A> dans la classe de base.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si l’opérateur d’égalité retourne la même valeur que l’implémentation héritée de <xref:System.Object.Equals%2A>. La section exemple comprend un type qui peut supprimer sans risque un avertissement de cette règle.

## <a name="examples-of-inconsistent-equality-definitions"></a>Exemples de définitions d’égalité incohérentes

### <a name="description"></a>Description
 L’exemple suivant montre un type avec des définitions d’égalité incohérentes. `BadPoint` modifie la signification de l’égalité en fournissant une implémentation personnalisée de l’opérateur d’égalité, mais ne substitue pas <xref:System.Object.Equals%2A> afin qu’il se comporte de manière identique.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorEqualsRequiresEquals/cs/FxCop.Usage.OperatorEqualsRequiresEquals.cs#1)]

## <a name="example"></a>Exemple
 Le code suivant teste le comportement de `BadPoint`.

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestOperatorEqualsRequiresEquals/cs/FxCop.Usage.TestOperatorEqualsRequiresEquals.cs#1)]

 Cet exemple produit la sortie suivante.

 **a = ([0] 1, 1) et b = ([1] 2, 2) sont égaux ? Non** 
**a = = b ? Aucun** 
**a1 et a ne sont égaux ? Oui** 
**a1 = = a ? Oui** 
**b et bcopy sont égaux ? Non** 
**b = = bcopy ? Oui**
## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui enfreint techniquement cette règle, mais qui ne se comporte pas de manière incohérente.

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ValueTypeEquals/cs/FxCop.Usage.ValueTypeEquals.cs#1)]

## <a name="example"></a>Exemple
 Le code suivant teste le comportement de `GoodPoint`.

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestValueTypeEquals/cs/FxCop.Usage.TestValueTypeEquals.cs#1)]

 Cet exemple produit la sortie suivante.

 **a = (1, 1) et b = (2, 2) sont égaux ? Non** 
**a = = b ? Aucun** 
**a1 et a ne sont égaux ? Oui** 
**a1 = = a ? Oui** 
**b et bcopy sont égaux ? Oui** 
**b = = bcopy ? Oui**
## <a name="class-example"></a>Exemple de classe

### <a name="description"></a>Description
 L’exemple suivant montre une classe (type référence) qui ne respecte pas cette règle.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassViolation/cs/FxCop.Usage.OverrideEqualsClassViolation.cs#1)]

## <a name="example"></a>Exemple
 L’exemple suivant résout la violation en remplaçant <xref:System.Object.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassFixed/cs/FxCop.Usage.OverrideEqualsClassFixed.cs#1)]

## <a name="structure-example"></a>Exemple de structure

### <a name="description"></a>Description
 L’exemple suivant illustre une structure (type valeur) qui enfreint cette règle.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructViolation/cs/FxCop.Usage.OverrideEqualsStructViolation.cs#1)]

## <a name="example"></a>Exemple
 L’exemple suivant résout la violation en remplaçant <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructFixed/cs/FxCop.Usage.OverrideEqualsStructFixed.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA1046 : Ne pas surcharger l’opérateur égal sur les types de référence](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225 : Les surcharges d’opérateur ont d’autres méthodes nommées](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226 : Les opérateurs doivent avoir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218 : Remplacez GetHashCode lors du remplacement de Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
