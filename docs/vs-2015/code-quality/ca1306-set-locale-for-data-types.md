---
title: 'CA1306 : définir les paramètres régionaux pour les types de données | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: edd1d6a7623f96f03403883ee2585d245414bb3b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539020"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306 : Définir les paramètres régionaux pour les types de données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Category|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode ou un constructeur a créé une ou plusieurs <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName> instances ou et n’a pas défini explicitement la propriété locale ( <xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> ou <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName> ).

## <a name="rule-description"></a>Description de la règle
 Les paramètres régionaux déterminent les éléments de présentation spécifiques à la culture pour les données, comme la mise en forme utilisée pour les valeurs numériques, les symboles monétaires et l’ordre de tri. Lorsque vous créez un <xref:System.Data.DataTable> ou un <xref:System.Data.DataSet> , vous devez définir les paramètres régionaux explicitement. Par défaut, les paramètres régionaux de ces types sont la culture actuelle. Pour les données stockées dans une base de données ou un fichier et qui sont partagées globalement, les paramètres régionaux doivent normalement être définis sur la culture dite indifférente ( <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> ). Lorsque les données sont partagées entre les cultures, l’utilisation des paramètres régionaux par défaut peut entraîner la <xref:System.Data.DataTable> <xref:System.Data.DataSet> présentation ou l’interprétation incorrecte du contenu de ou.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, définissez explicitement les paramètres régionaux pour <xref:System.Data.DataTable> ou <xref:System.Data.DataSet> .

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle lorsque la bibliothèque ou l’application est destinée à une audience locale limitée, que les données ne sont pas partagées ou que le paramètre par défaut produit le comportement souhaité dans tous les scénarios pris en charge.

## <a name="example"></a>Exemple
 L’exemple suivant crée deux <xref:System.Data.DataTable> instances de.

 [!code-csharp[FxCop.Globalization.DataTable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DataTable/cs/FxCop.Globalization.DataTable.cs#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>
