---
title: 'Ca1717 : seuls les noms des enums FlagsAttribute doivent être au pluriel | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c58c218991226a954185853097dc81da36c69ed6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543687"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717 : Seuls les noms des enums FlagsAttribute doivent être au pluriel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Category|Microsoft. Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause :
 Le nom d’une énumération visible de l’extérieur se termine par un mot pluriel et l’énumération n’est pas marquée avec l' <xref:System.FlagsAttribute?displayProperty=fullName> attribut.

## <a name="rule-description"></a>Description de la règle
 Les conventions d’affectation de noms stipulent qu’un nom au pluriel pour une énumération indique qu’il est possible de spécifier plusieurs valeurs de l’énumération simultanément. Le <xref:System.FlagsAttribute> indique aux compilateurs que l’énumération doit être traitée comme un champ de bits qui active des opérations au niveau du bit sur l’énumération.

 Si une seule valeur d’une énumération peut être spécifiée à la fois, le nom de l’énumération doit être un mot singulier. Par exemple, une énumération qui définit les jours de la semaine peut être destinée à être utilisée dans une application où vous pouvez spécifier plusieurs jours. Cette énumération doit avoir la <xref:System.FlagsAttribute> et peut être appelée « Days ». Une énumération similaire qui autorise la spécification d’un seul jour n’a pas l’attribut et peut être appelée « Day ».

 Les conventions d’affectation de noms fournissent une recherche commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit le temps nécessaire à l’apprentissage d’une nouvelle bibliothèque de logiciels et augmente la confiance des clients dans le développement de la bibliothèque par une personne expérimentée dans le développement de code géré.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Faites du nom de l’énumération un mot au singulier ou ajoutez <xref:System.FlagsAttribute> .

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de la règle si le nom se termine par un mot au singulier.

## <a name="related-rules"></a>Règles associées
 [CA1714 : Les noms des enums Flags doivent être au pluriel](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027 : Marquer les enums avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217 : Ne marquez pas les enums avec l'attribut FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.FlagsAttribute?displayProperty=fullName>[Conception d’énumération](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
