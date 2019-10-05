---
title: "CA2243 : Les littéraux de chaîne d'attribut doivent être analysés correctement"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2627e94dbdd0504b164fee3ecd95dc99b3094db7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237819"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243 : Les littéraux de chaîne d'attribut doivent être analysés correctement

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Le paramètre de littéral de chaîne d’un attribut n’est pas analysé correctement pour une URL, un GUID ou une version.

## <a name="rule-description"></a>Description de la règle
Étant donné que les attributs <xref:System.Attribute?displayProperty=fullName>sont dérivés de, et que les attributs sont utilisés au moment de la compilation, seules les valeurs constantes peuvent être passées à leurs constructeurs. Les paramètres d’attribut qui doivent représenter des URL, des GUID et des versions ne <xref:System.Uri?displayProperty=fullName>peuvent <xref:System.Guid?displayProperty=fullName>pas être <xref:System.Version?displayProperty=fullName>de type, et, car ces types ne peuvent pas être représentés en tant que constantes. Au lieu de cela, elles doivent être représentées par des chaînes.

Étant donné que le paramètre est tapé sous la forme d’une chaîne, il est possible qu’un paramètre mis en forme de manière incorrecte soit passé au moment de la compilation.

Cette règle utilise une heuristique d’attribution de noms pour rechercher des paramètres qui représentent un URI (Uniform Resource Identifier), un identificateur global unique (GUID) ou une version, et vérifie que la valeur passée est correcte.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Remplacez la chaîne de paramètres par une URL, un GUID ou une version correctement formé (e).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle si le paramètre ne représente pas une URL, un GUID ou une version.

## <a name="example"></a>Exemple
L’exemple suivant montre le code pour le AssemblyFileVersionAttribute qui enfreint cette règle.

[!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]

La règle est déclenchée par les paramètres suivants :

- Les paramètres qui contiennent « version » et ne peuvent pas être analysés dans System. version.

- Les paramètres qui contiennent « GUID » et ne peuvent pas être analysés dans System. Guid.

- Les paramètres qui contiennent « URI », « urn » ou « URL » et ne peuvent pas être analysés sur System. Uri.

## <a name="see-also"></a>Voir aussi

- [CA1054 Les paramètres URI ne doivent pas être des chaînes](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)