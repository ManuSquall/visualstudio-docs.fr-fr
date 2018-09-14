---
title: "CA2243 : Les littéraux de chaîne d'attribut doivent être correctement analysés"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c6808520f3b28a2da8421394619550166d88d52d
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551936"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243 : Les littéraux de chaîne d'attribut doivent être correctement analysés

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Paramètre de littéral de chaîne d’un attribut n’analyse pas correctement pour une URL, un GUID ou une Version.

## <a name="rule-description"></a>Description de la règle
 Dans la mesure où les attributs sont dérivés de <xref:System.Attribute?displayProperty=fullName>et ils sont utilisés au moment de la compilation, seules des valeurs constantes peuvent être passées à leurs constructeurs. Paramètres d’attribut qui doivent représenter des URL, des GUID et des Versions ne peut pas être de type <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName>, et <xref:System.Version?displayProperty=fullName>, car ces types ne peuvent pas être représentés en tant que constantes. Au lieu de cela, ils doivent être représentées par des chaînes.

 Étant donné que le paramètre est typé en tant que chaîne, il est possible qu’un paramètre au format incorrect peut être passé au moment de la compilation.

 Cette règle utilise une heuristique d’affectation de noms pour rechercher des paramètres qui représentent un identificateur de ressource uniforme (URI), un identificateur global Unique (GUID) ou une Version et vérifie que la valeur passée est correcte.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Modifier la chaîne de paramètre à une URL, GUID ou Version correctement formé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si le paramètre ne représente pas une URL, un GUID ou une Version sans.

## <a name="example"></a>Exemple
 L’exemple suivant montre le code de l’AssemblyFileVersionAttribute qui enfreint cette règle.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]

 La règle est déclenchée par les paramètres suivants :

- Paramètres qui contiennent « version » et ne peut pas être analysées à System.Version.

- Paramètres qui contiennent des 'guid' et ne peut pas être analysées à System.Guid.

- Paramètres qui contiennent « uri », « urn » ou « url » et ne peut pas être analysées en System.Uri.

## <a name="see-also"></a>Voir aussi

- [CA1054 : Les paramètres d’URI ne doivent pas être des chaînes](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)