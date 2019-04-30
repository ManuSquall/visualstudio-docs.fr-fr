---
title: 'CA1043 : Utiliser un argument de chaîne ou intégral pour les indexeurs'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3d47b39208fce297fd058d6976b9fa7d7593cb9a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778798"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043 : Utiliser un argument de chaîne ou intégral pour les indexeurs

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un type contient un indexeur qui utilise un type d’index autre que <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, ou <xref:System.String?displayProperty=fullName>.

Par défaut, cette règle examine uniquement les types publics et protégés, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

Les indexeurs, autrement dit, les propriétés indexées, doivent utiliser des types entier ou chaîne pour l’index. Ces types sont généralement utilisés pour indexer des structures de données et augmentent la facilité d’utilisation de la bibliothèque. Utilisation de la <xref:System.Object> type doit être limité aux cas où le type entier ou une chaîne spécifique ne peut pas être spécifié au moment du design. Si la conception nécessite d’autres types pour l’index, reconsidérez si le type représente un magasin de données logique. Si elle ne représente pas un magasin de données logique, utilisez une méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, modifier l’index à un type entier ou chaîne, ou utilisez une méthode au lieu de l’indexeur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Supprimer un avertissement de cette règle uniquement après avoir soigneusement envisagé la nécessité de l’indexeur non standard.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```
dotnet_code_quality.ca1043.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un indexeur qui utilise un <xref:System.Int32> index.

[!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
[!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
[!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]

## <a name="related-rules"></a>Règles associées

- [CA1023 : Les indexeurs ne doivent pas être multidimensionnels](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)
- [CA1024 : Utiliser des propriétés lorsque nécessaire](../code-quality/ca1024-use-properties-where-appropriate.md)