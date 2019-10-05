---
title: 'CA1720 : Les identificateurs ne doivent pas contenir de noms de types'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2677c2ef5342b795bb684f3ab06bc7cf5195cf7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233896"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720 : Les identificateurs ne doivent pas contenir de noms de types

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Le nom d’un paramètre dans un membre contient un nom de type de données.

\- ou -

Le nom d’un membre contient un nom de type de données spécifique à une langue.

Par défaut, cette règle recherche uniquement les membres visibles de l’extérieur, mais elle peut [être configurée](#configurability).

## <a name="rule-description"></a>Description de la règle

Les noms des paramètres et des membres sont mieux utilisés pour communiquer leur signification que pour décrire leur type, qui devrait être fourni par les outils de développement. Pour les noms de membres, si un nom de type de données doit être utilisé, utilisez un nom indépendant du langage au lieu d’un nom spécifique à une langue. Par exemple, à la place C# du nom `int`de type, utilisez le nom de type de `Int32`données indépendant du langage.

Chaque jeton discret dans le nom du paramètre ou du membre est vérifié par rapport aux noms de types de données spécifiques à la langue suivants, sans respect de la casse :

- Bool
- WChar
- Int8
- UInt8
- Courte
- UShort
- Int
- UInt
- Entier
- UInteger
- Longue
- ULong
- Non signé
- Signé
- Float
- Float32
- Float64

En outre, les noms d’un paramètre sont également vérifiés par rapport aux noms de types de données indépendants du langage suivants sans respect de la casse :

- Object
- Obj
- Booléen
- Char
- Chaîne
- SByte
- Byte
- UByte
- Int16
- UInt16
- Int32
- UInt32
- Int64
- UInt64
- IntPtr
- effectués
- Pointeur
- UInptr
- UPtr
- UPointer
- Single
- Double
- Decimal
- GUID

## <a name="how-to-fix-violations"></a>Comment corriger les violations

**En cas de déclenchement sur un paramètre :**

Remplacez l’identificateur de type de données dans le nom du paramètre par un terme qui décrit mieux sa signification ou un terme plus générique, tel que « value ».

**En cas de déclenchement sur un membre :**

Remplacez l’identificateur de type de données spécifique au langage dans le nom du membre par un terme qui décrit mieux sa signification, un équivalent indépendant du langage ou un terme plus générique, tel que « value ».

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

L’utilisation occasionnelle des noms de paramètres et de membres basés sur le type peut être appropriée. Toutefois, pour un nouveau développement, aucun scénario connu ne se produit lorsque vous devez supprimer un avertissement de cette règle. Pour les bibliothèques qui ont déjà été expédiées, vous devrez peut-être supprimer un avertissement de cette règle.

## <a name="configurability"></a>Configurabilité

Si vous exécutez cette règle à partir d' [analyseurs FxCop](install-fxcop-analyzers.md) (et non avec l’analyse héritée), vous pouvez configurer les parties de votre code base sur lesquelles exécuter cette règle, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet :

```ini
dotnet_code_quality.ca1720.api_surface = private, internal
```

Vous pouvez configurer cette option uniquement pour cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (affectation de noms). Pour plus d’informations, consultez [configurer les analyseurs FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Règles associées

- [CA1709 La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708 Les identificateurs ne doivent pas différer uniquement par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707 Les identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1719 Les noms des paramètres ne doivent pas correspondre aux noms des membres](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)