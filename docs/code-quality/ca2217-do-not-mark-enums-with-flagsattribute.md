---
title: 'CA2217 : Ne pas marquer les enums avec FlagsAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
dev_langs:
- VB
- CSharp
- CPP
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12cc5f9fc58ac533d118b693587cf807f44b288f
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217 : Ne pas marquer les enums avec FlagsAttribute

|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une énumération extérieurement visible est marquée avec <xref:System.FlagsAttribute>et possède une ou plusieurs valeurs qui ne sont pas des puissances de deux ou une combinaison de l’autre définition des valeurs dans l’énumération.

## <a name="rule-description"></a>Description de la règle

Une énumération doit avoir <xref:System.FlagsAttribute> présent uniquement si chaque valeur définie dans l’énumération est une puissance de deux ou une combinaison de définition des valeurs.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, supprimez <xref:System.FlagsAttribute> à partir de l’énumération.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle.

## <a name="example-that-should-not-have-the-attribute"></a>Exemple de l’attribut ne doit pas être

L’exemple suivant montre une énumération, `Color`, qui contient la valeur 3. 3 n’est pas une puissance de deux ou une combinaison d’une des valeurs définies. Le `Color` énumération ne doit pas être marquée avec <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

## <a name="example-that-should-have-the-attribute"></a>Exemple qui doit avoir l’attribut

L’exemple suivant montre une énumération, `Days`, qui répond aux exigences du est marqué comme étant avec <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>Règles associées

[CA1027 : Marquez les énumérations avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.FlagsAttribute?displayProperty=fullName>
