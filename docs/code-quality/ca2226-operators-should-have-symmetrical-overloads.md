---
title: 'CA2226 : Les opérateurs doivent contenir des surcharges symétriques'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4557b61afab08c7db05c734c6f2ac927a40edb71
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546851"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226 : Les opérateurs doivent contenir des surcharges symétriques

|||
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type implémente l'opérateur d'égalité ou d'inégalité et n'implémente pas l'opérateur opposé.

Par défaut, cette règle recherche uniquement les types visibles de l’extérieur, mais elle peut [être configurée](#configurability).

## <a name="rule-description"></a>Description de la règle

Il n’existe aucune circonstance dans laquelle l’égalité ou l’inégalité est applicable aux instances d’un type, et l’opérateur opposé n’est pas défini. Les types implémentent généralement l’opérateur d’inégalité en retournant la valeur de négation de l’opérateur d’égalité.

Le C# compilateur émet une erreur pour les violations de cette règle.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, implémentez à la fois les opérateurs d’égalité et d’inégalité, ou supprimez celui qui est présent.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle. Si vous le faites, votre type ne fonctionnera pas de manière cohérente avec .NET.

## <a name="configurability"></a>Configurabilité

Si vous exécutez cette règle à partir d' [analyseurs FxCop](install-fxcop-analyzers.md) (et non avec l’analyse héritée), vous pouvez configurer les parties de votre code base sur lesquelles exécuter cette règle, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet:

```ini
dotnet_code_quality.ca2226.api_surface = private, internal
```

Vous pouvez configurer cette option uniquement pour cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (utilisation). Pour plus d’informations, consultez [configurer les analyseurs FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Règles associées

- [CA1046 Ne pas surcharger l’opérateur égal à sur les types référence](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2225 Les surcharges d’opérateur ont des alternatives nommées](../code-quality/ca2225-operator-overloads-have-named-alternates.md)
- [CA2224 Remplacer Equals lors de la surcharge de l’opérateur égal](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218 Substituez GetHashCode lors du remplacement d’égal](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)