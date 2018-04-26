---
title: 'CA1720 : Les identificateurs ne doivent pas contenir de noms de types'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a8f86037b54b2b7ad5cce1ea683341ca6656c2b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720 : Les identificateurs ne doivent pas contenir de noms de types
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
 Noms de paramètres et les membres sont mieux utilisés pour communiquer leur signification que to décrire leur type, qui doit être fournie par les outils de développement. Pour les noms de membres, si un nom de type de données doit être utilisé, utilisez un nom indépendant du langage au lieu d’une langue spécifique. Par exemple, au lieu du nom de type c# 'int', utilisez le nom de type de données indépendant du langage, Int32.

 Chaque jeton discret dans le nom du paramètre ou le membre est comparée aux noms de types de données spécifiques au langage suivants, sans respecter la casse :

-   Bool

-   WChar

-   Int8

-   UInt8

-   Courte

-   UShort

-   Int

-   UInt

-   Entier

-   UInteger

-   Longue

-   ULong

-   Non signé

-   Signé

-   Float

-   Float32

-   Float64

 En outre, les noms d’un paramètre sont également vérifiés par rapport aux noms de types de données indépendant du langage suivants, sans respecter la casse :

-   Object

-   obj

-   Booléen

-   Char

-   Chaîne

-   SByte

-   Byte

-   UByte

-   Int16

-   UInt16

-   Int32

-   UInt32

-   Int64

-   UInt64

-   IntPtr

-   PTR

-   Pointeur

-   UInptr

-   UPtr

-   UPointer

-   Single

-   Double

-   Decimal

-   GUID

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 **Si le déclenchement sur un paramètre :**

 Remplacez l’identificateur de type de données dans le nom du paramètre par un terme qui décrit mieux sa signification ou par un terme plus générique, tel que 'value'.

 **Si le déclenchement sur un membre :**

 Remplacez l’identificateur de type de données spécifiques au langage dans le nom du membre par un terme qui décrit mieux sa signification, un équivalent indépendant du langage ou un terme plus générique, tel que 'value'.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 L’utilisation occasionnelle de noms de membre et de paramètre basée sur le type peut être appropriée. Toutefois, pour un nouveau développement, aucun autre scénarios se produisent lorsque vous ne devez supprimer un avertissement de cette règle. Pour les bibliothèques déjà livrées, vous devrez peut-être supprimer un avertissement de cette règle.

## <a name="related-rules"></a>Règles associées
 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708 : Les identificateurs ne doivent pas différer que par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719 : Les noms des paramètres ne doivent pas être identiques aux noms des membres](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)