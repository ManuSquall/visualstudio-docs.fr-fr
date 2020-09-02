---
title: 'CA2217 : ne Marquez pas les enums avec FlagsAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b584e355f5b64984f57dd17606dfb0a2f781c62d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547665"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217 : Ne marquez pas les enums avec l'attribut FlagsAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Une énumération visible de l’extérieur est marquée avec <xref:System.FlagsAttribute> et elle a une ou plusieurs valeurs qui ne sont pas des puissances de deux ou une combinaison des autres valeurs définies sur l’énumération.

## <a name="rule-description"></a>Description de la règle
 Une énumération doit être <xref:System.FlagsAttribute> présente uniquement si chaque valeur définie dans l’énumération est une puissance de deux ou une combinaison de valeurs définies.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez <xref:System.FlagsAttribute> de l’énumération.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant illustre une énumération, Color, qui contient la valeur 3, qui n’est ni une puissance de deux, ni une combinaison de l’une des valeurs définies. L’énumération de couleur ne doit pas être marquée avec <xref:System.FlagsAttribute> .

 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/cpp/FxCop.Usage.EnumNoFlags.cpp#1)]
 [!code-csharp[FxCop.Usage.EnumNoFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/cs/FxCop.Usage.EnumNoFlags.cs#1)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/vb/FxCop.Usage.EnumNoFlags.vb#1)]

## <a name="example"></a>Exemple
 L’exemple suivant montre une énumération, Days, qui remplit les conditions requises pour être marquée avec System. FlagsAttribute.

 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/cpp/FxCop.Usage.EnumNoFlags2.cpp#1)]
 [!code-csharp[FxCop.Usage.EnumNoFlags2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/cs/FxCop.Usage.EnumNoFlags2.cs#1)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/vb/FxCop.Usage.EnumNoFlags2.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1027 : Marquer les enums avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.FlagsAttribute?displayProperty=fullName>
