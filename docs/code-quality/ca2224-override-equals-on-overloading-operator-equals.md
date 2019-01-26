---
title: "CA2224 : Remplacez Equals au moment de surcharger l'opérateur égal"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eac7f403cd0e115a01252537ade45e6a1bc0aaad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957882"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224 : Remplacez Equals au moment de surcharger l'opérateur égal

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type public implémente l’opérateur d’égalité, mais ne remplace pas <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle

L’opérateur d’égalité est destinée à être un point de vue syntaxique pour accéder facilement les fonctionnalités de la <xref:System.Object.Equals%2A> (méthode). Si vous implémentez l’opérateur d’égalité, sa logique doit être identique à celle de <xref:System.Object.Equals%2A>.

Le compilateur c# émet un avertissement si votre code ne respecte pas cette règle.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, vous devez supprimer l’implémentation de l’opérateur d’égalité ou substituer <xref:System.Object.Equals%2A> et avoir les deux méthodes retournent les mêmes valeurs. Si l’opérateur d’égalité n’introduit pas de comportement incohérent, vous pouvez corriger la violation en fournissant une implémentation de <xref:System.Object.Equals%2A> qui appelle le <xref:System.Object.Equals%2A> méthode dans la classe de base.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle si l’opérateur d’égalité retourne la même valeur que l’implémentation héritée de <xref:System.Object.Equals%2A>. Les exemples dans cet article incluent un type qui pourrait supprimer sans risque un avertissement de cette règle.

## <a name="examples-of-inconsistent-equality-definitions"></a>Exemples de définitions d’égalité incohérentes

L’exemple suivant illustre un type avec des définitions d’égalité incohérentes. `BadPoint` Modifie la signification de l’égalité en fournissant une implémentation personnalisée de l’opérateur d’égalité, mais ne se substitue pas <xref:System.Object.Equals%2A> afin qu’il a un comportement identique.

[!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

Le code suivant teste le comportement de `BadPoint`.

[!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]

Cet exemple génère la sortie suivante :

```txt
a =  ([0] 1,1) and b = ([1] 2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? No
b == bcopy ? Yes
```

L’exemple suivant illustre un type qui techniquement enfreint cette règle, mais ne se comporte pas de façon incohérente.

[!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

Le code suivant teste le comportement de `GoodPoint`.

[!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]

Cet exemple génère la sortie suivante :

```txt
a =  (1,1) and b = (2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? Yes
b == bcopy ? Yes
```

## <a name="class-example"></a>Exemple de classe

L’exemple suivant montre une classe (type référence) qui enfreint cette règle.

[!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

L’exemple suivant résout la violation en substituant <xref:System.Object.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>Exemple de structure

L’exemple suivant montre une structure (type valeur) qui enfreint cette règle :

[!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

L’exemple suivant résout la violation en substituant <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>Règles associées

[CA1046 : Ne pas surcharger l’opérateur égal sur les types référence](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225 : Surcharges d’opérateur ont d’autres méthodes nommées](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226 : Les opérateurs doivent contenir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2218 : Remplacez GetHashCode au moment de remplacer Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

[CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)