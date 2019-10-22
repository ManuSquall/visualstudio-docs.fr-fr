---
title: 'Ca1720 : les identificateurs ne doivent pas contenir de noms de types | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 34ebe4848bbbe49b9a67449795f0aea7d104af8b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671639"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720 : Les identificateurs ne doivent pas contenir de noms de types
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Category|Microsoft. Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le nom d’un paramètre dans un membre visible de l’extérieur contient un nom de type de données.

 ou

 Le nom d’un membre visible de l’extérieur contient un nom de type de données spécifique à une langue.

## <a name="rule-description"></a>Description de la règle
 Les noms des paramètres et des membres sont mieux utilisés pour communiquer leur signification que pour décrire leur type, qui devrait être fourni par les outils de développement. Pour les noms de membres, si un nom de type de données doit être utilisé, utilisez un nom indépendant du langage au lieu d’un nom spécifique à une langue. Par exemple, au lieu du C# nom de type’int', utilisez le nom de type de données indépendant du langage, Int32.

 Chaque jeton discret dans le nom du paramètre ou du membre est vérifié par rapport aux noms de types de données spécifiques au langage suivants, sans respect de la casse :

- Bool

- WChar

- Int8

- UInt8

- Courte

- UShort

- int

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

  En outre, les noms d’un paramètre sont également vérifiés par rapport aux noms de types de données indépendants du langage suivants, sans respect de la casse :

- Objet

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

- Effectués

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
 L’utilisation occasionnelle des noms de paramètres et de membres basés sur le type peut être appropriée. Toutefois, pour un nouveau développement, aucun scénario connu ne se produit lorsque vous devez supprimer un avertissement de cette règle. Pour les bibliothèques qui ont été expédiées précédemment, vous devrez peut-être supprimer un avertissement de cette règle.

## <a name="related-rules"></a>Règles associées
 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708 : Les identificateurs ne doivent pas différer que par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719 : Les noms des paramètres ne doivent pas être identiques aux noms des membres](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)
