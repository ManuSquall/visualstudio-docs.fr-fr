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
ms.openlocfilehash: c596ddfa36beec696c275ea13b662ceebf8bde2c
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841792"
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

ou

Le nom d’un membre contient un nom de type de données spécifiques au langage.

Par défaut, cette règle examine uniquement les membres visibles de l’extérieur, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

Noms de paramètres et les membres sont mieux utilisés pour communiquer leur signification que to décrire leur type, ce qui devrait être fourni par les outils de développement. Pour les noms de membres, si un nom de type de données doit être utilisé, utilisez un nom indépendant du langage au lieu d’une langue spécifique. Par exemple, au lieu du C# nom de type `int`, utilisez le nom de type de données indépendant du langage, `Int32`.

Chaque jeton discret dans le nom de paramètre ou de membre est comparée aux noms de types de données spécifiques au langage suivants casse :

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

En outre, les noms d’un paramètre sont également vérifiés parmi les noms de type de données indépendant du langage suivant casse :

- Object
- obj
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
- PTR
- Pointeur
- UInptr
- UPtr
- UPointer
- Single
- Double
- Decimal
- GUID

## <a name="how-to-fix-violations"></a>Comment corriger les violations

**Si le déclenchement sur un paramètre :**

Remplacez l’identificateur de type de données dans le nom du paramètre par un terme qui décrit mieux sa signification ou par un terme plus générique, tel que 'value'.

**Si le déclenchement sur un membre :**

Remplacez l’identificateur de type de données spécifiques au langage dans le nom du membre par un terme qui décrit mieux sa signification, un équivalent indépendant du langage ou un terme plus générique, tel que 'value'.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Utilisation occasionnelle de noms de paramètres et de membres en fonction de type peut être appropriée. Toutefois, pour un nouveau développement, aucun connus scénarios se produisent dans lequel vous ne devez supprimer un avertissement de cette règle. Pour les bibliothèques fournies antérieurement, vous devrez peut-être supprimer un avertissement de cette règle.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```ini
dotnet_code_quality.ca1720.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (d’affectation de noms). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Règles associées

- [CA1709 : Identificateurs doivent être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708 : Les identificateurs doivent différer par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707 : Identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1719 : Noms de paramètres ne doivent pas correspondre aux noms de membres](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)