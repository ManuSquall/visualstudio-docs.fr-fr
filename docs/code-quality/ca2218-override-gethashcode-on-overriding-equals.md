---
title: 'CA2218 : Remplacez GetHashCode au moment de remplacer Equals'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2218
- OverrideGetHashCodeOnOverridingEquals
helpviewer_keywords:
- OverrideGetHashCodeOnOverridingEquals
- CA2218
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5dbd8580f5aaeb88c08d35b50258510cb1a85ba2
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920288"
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218 : Remplacez GetHashCode au moment de remplacer Equals

|||
|-|-|
|TypeName|OverrideGetHashCodeOnOverridingEquals|
|CheckId|CA2218|
|Catégorie|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Un type public substitue <xref:System.Object.Equals%2A?displayProperty=fullName> mais ne remplace <xref:System.Object.GetHashCode%2A?displayProperty=fullName>pas.

## <a name="rule-description"></a>Description de la règle
 <xref:System.Object.GetHashCode%2A>retourne une valeur, basée sur l’instance actuelle, qui convient aux algorithmes de hachage et aux structures de données telles qu’une table de hachage. Deux objets du même type et sont égaux doivent retourner le même code de hachage pour s’assurer que les instances des types suivants fonctionnent correctement:

- <xref:System.Collections.Hashtable?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

- Types qui implémentent<xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, fournissez une implémentation <xref:System.Object.GetHashCode%2A>de. Pour une paire d’objets du même type, vous devez vous assurer que l’implémentation retourne la même valeur si votre implémentation de <xref:System.Object.Equals%2A> retourne `true` pour la paire.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="class-example"></a>Exemple de classe

### <a name="description"></a>Description
L’exemple suivant montre une classe (type référence) qui ne respecte pas cette règle.

### <a name="code"></a>Code
[!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]

### <a name="comments"></a>Commentaires
L’exemple suivant résout la violation en remplaçant <xref:System.Object.GetHashCode>.

### <a name="code"></a>Code
[!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]

## <a name="structure-example"></a>Exemple de structure

### <a name="description"></a>Description
L’exemple suivant illustre une structure (type valeur) qui enfreint cette règle.

### <a name="code"></a>Code
[!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]

### <a name="comments"></a>Commentaires
L’exemple suivant résout la violation en remplaçant <xref:System.Object.GetHashCode>.

### <a name="code"></a>Code
[!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_4.cs)]

## <a name="related-rules"></a>Règles associées
[CA1046 Ne pas surcharger l’opérateur égal à sur les types référence](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225 Les surcharges d’opérateur ont des alternatives nommées](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226 Les opérateurs doivent avoir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2224 Remplacer Equals lors de la surcharge de l’opérateur égal](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

[CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- <xref:System.Object.GetHashCode%2A?displayProperty=fullName>
- <xref:System.Collections.Hashtable?displayProperty=fullName>
- [Opérateurs d’égalité](/dotnet/standard/design-guidelines/equality-operators)