---
title: 'CA2243 : les littéraux de chaîne d’attribut doivent être analysés correctement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 09e932651576f9b6d595657ad024b8f2697ad016
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535744"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243 : Les littéraux de chaîne d'attribut doivent être analysés correctement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Le paramètre de littéral de chaîne d’un attribut n’est pas analysé correctement pour une URL, un GUID ou une version.

## <a name="rule-description"></a>Description de la règle
 Étant donné que les attributs sont dérivés de <xref:System.Attribute?displayProperty=fullName> , et que les attributs sont utilisés au moment de la compilation, seules les valeurs constantes peuvent être passées à leurs constructeurs. Les paramètres d’attribut qui doivent représenter des URL, des GUID et des versions ne peuvent pas être de type <xref:System.Uri?displayProperty=fullName> , <xref:System.Guid?displayProperty=fullName> et <xref:System.Version?displayProperty=fullName> , car ces types ne peuvent pas être représentés en tant que constantes. Au lieu de cela, elles doivent être représentées par des chaînes.

 Étant donné que le paramètre est tapé sous la forme d’une chaîne, il est possible qu’un paramètre mis en forme de manière incorrecte soit passé au moment de la compilation.

 Cette règle utilise une méthode heuristique d’attribution de noms pour rechercher des paramètres qui représentent un URI (Uniform Resource Identifier), un identificateur global unique (GUID) ou une version et vérifie que la valeur passée est correcte.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Remplacez la chaîne de paramètres par une URL, un GUID ou une version correctement formé (e).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si le paramètre ne représente pas une URL, un GUID ou une version.

## <a name="example"></a>Exemple
 L’exemple suivant montre le code pour le AssemblyFileVersionAttribute qui enfreint cette règle.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]

 La règle est déclenchée par les éléments suivants :

- Les paramètres qui contiennent « version » et ne peuvent pas être analysés dans System. version.

- Les paramètres qui contiennent « GUID » et ne peuvent pas être analysés dans System. Guid.

- Les paramètres qui contiennent « URI », « urn » ou « URL » et ne peuvent pas être analysés sur System. Uri.

## <a name="see-also"></a>Voir aussi
 [CA1054 : Les paramètres URI ne doivent pas être des chaînes](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
