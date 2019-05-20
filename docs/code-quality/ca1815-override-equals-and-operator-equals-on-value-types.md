---
title: "CA1815 : Remplacez Equals et l'opérateur égal à dans les types valeur"
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58d746b022d5cc3f67b53e1dc845d81bf8409ec6
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841481"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815 : Remplacez Equals et l'opérateur égal à dans les types valeur

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Category|Microsoft.Performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type valeur ne remplace pas <xref:System.Object.Equals%2A?displayProperty=fullName> ou n’implémente pas l’opérateur d’égalité (==). Cette règle ne vérifie pas les énumérations.

Par défaut, cette règle examine uniquement les types visibles de l’extérieur, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

Pour les types valeur, l’implémentation héritée de <xref:System.Object.Equals%2A> utilise la bibliothèque Reflection et compare le contenu de tous les champs. Le processus de réflexion sollicite fortement les ressources informatiques et la comparaison de chaque champ à la recherche d'une égalité peut s'avérer inutile. Si vous prévoyez que les utilisateurs à comparer ou trier des instances, ou les utilisez en tant que clés de table de hachage, votre type valeur doit implémenter <xref:System.Object.Equals%2A>. Si votre langage de programmation prend en charge la surcharge des opérateurs, vous devez également fournir une implémentation des opérateurs d’égalité et d’inégalité.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, fournir une implémentation de <xref:System.Object.Equals%2A>. Si vous pouvez implémenter l’opérateur d’égalité.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle si les instances du type valeur ne seront pas comparer à l’autre sans.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```ini
dotnet_code_quality.ca1815.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (performances). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemple

Le code suivant montre une structure (type valeur) qui enfreint cette règle :

[!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]

Le code suivant corrige la violation précédente en substituant <xref:System.ValueType.Equals%2A?displayProperty=fullName> et en implémentant les opérateurs d’égalité (==, ! =) :

[!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]

## <a name="related-rules"></a>Règles associées

- [CA2224 : Remplacez equals lors de la surcharge l’opérateur égal](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
- [CA2226 : Les opérateurs doivent contenir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.Object.Equals%2A?displayProperty=fullName>