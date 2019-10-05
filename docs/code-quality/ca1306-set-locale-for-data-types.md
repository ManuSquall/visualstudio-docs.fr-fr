---
title: 'CA1306 : Définir les paramètres régionaux pour les types de données'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aaf16ccd187681be7406fdadbde620a167a40c96
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235024"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306 : Définir les paramètres régionaux pour les types de données

|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Category|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Une méthode ou un constructeur a créé une <xref:System.Data.DataTable?displayProperty=fullName> ou <xref:System.Data.DataSet?displayProperty=fullName> plusieurs instances ou et n’a pas défini explicitement la propriété<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> locale <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>(ou).

## <a name="rule-description"></a>Description de la règle
Les paramètres régionaux déterminent les éléments de présentation spécifiques à la culture pour les données, comme la mise en forme utilisée pour les valeurs numériques, les symboles monétaires et l’ordre de tri. Lorsque vous créez un <xref:System.Data.DataTable> ou <xref:System.Data.DataSet>un, vous devez définir les paramètres régionaux explicitement. Par défaut, les paramètres régionaux de ces types sont la culture actuelle. Pour les données stockées dans une base de données ou un fichier et qui sont partagées globalement, les paramètres régionaux doivent normalement être définis sur la culture dite<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>indifférente (). Lorsque les données sont partagées entre les cultures, l’utilisation des paramètres régionaux par défaut peut <xref:System.Data.DataTable> entraîner <xref:System.Data.DataSet> la présentation ou l’interprétation incorrecte du contenu de ou.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, définissez explicitement les paramètres régionaux pour <xref:System.Data.DataTable> ou. <xref:System.Data.DataSet>

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle lorsque la bibliothèque ou l’application est destinée à une audience locale limitée, que les données ne sont pas partagées ou que le paramètre par défaut produit le comportement souhaité dans tous les scénarios pris en charge.

## <a name="example"></a>Exemple
L’exemple suivant crée deux <xref:System.Data.DataTable> instances de.

[!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataTable?displayProperty=fullName>
- <xref:System.Data.DataSet?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>