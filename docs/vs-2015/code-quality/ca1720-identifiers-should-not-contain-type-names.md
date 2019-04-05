---
title: 'CA1720 : Identificateurs ne doivent pas contenir les noms de type | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 504c985bd276a891b76e8c9b2a7c0ef51c3a490a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951505"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720 : Les identificateurs ne doivent pas contenir de noms de types
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le nom d’un paramètre dans un membre extérieurement visible contient un nom de type de données.

 - ou -

 Le nom d’un membre extérieurement visible contient un nom de type de données spécifiques au langage.

## <a name="rule-description"></a>Description de la règle
 Noms de paramètres et les membres sont mieux utilisés pour communiquer leur signification que to décrire leur type, ce qui devrait être fourni par les outils de développement. Pour les noms de membres, si un nom de type de données doit être utilisé, utilisez un nom indépendant du langage au lieu d’une langue spécifique. Par exemple, au lieu du nom de type c# 'int', utilisez le nom de type de données indépendant du langage, Int32.

 Chaque jeton discret dans le nom de paramètre ou de membre est comparée aux noms de types de données spécifiques au langage suivants, casse :

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

  En outre, les noms d’un paramètre sont également vérifiés par rapport à des noms de type de données indépendant du langage suivants, casse :

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
 Utilisation occasionnelle de noms de paramètres et de membres en fonction de type peut être appropriée. Toutefois, pour un nouveau développement, aucun connus scénarios se produisent dans lequel vous ne devez supprimer un avertissement de cette règle. Pour les bibliothèques déjà livrées, vous devrez peut-être supprimer un avertissement de cette règle.

## <a name="related-rules"></a>Règles associées
 [CA1709 : Identificateurs doivent être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708 : Les identificateurs doivent différer par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707 : Identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719 : Noms de paramètres ne doivent pas correspondre aux noms de membres](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)
