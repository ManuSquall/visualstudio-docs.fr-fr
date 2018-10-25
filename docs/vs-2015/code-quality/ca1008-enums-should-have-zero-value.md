---
title: 'CA1008 : Les Enums doivent avoir la valeur zéro | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 69e60b0f2ee8106b04507722f1b3094e1bbdbbc8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874824"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008 : Les enums doivent avoir la valeur zéro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture - lorsque vous êtes invité à ajouter un **aucun** valeur à une énumération sans indicateur. Avec rupture - lorsque vous êtes invité à les renommer ou supprimer des valeurs d’énumération.|

## <a name="cause"></a>Cause
 Une énumération sans un appliqué <xref:System.FlagsAttribute?displayProperty=fullName> ne définit pas un membre qui a comme valeur de zéro ; ou une énumération qui a une appliqué <xref:System.FlagsAttribute> définit un membre qui a une valeur égale à zéro, mais son nom n’est pas 'None', ou l’énumération définit plusieurs valeur zéro membres.

## <a name="rule-description"></a>Description de la règle
 La valeur par défaut d’une énumération non initialisée, tout comme les autres types de valeur est égale à zéro. Une énumération attribuée sans indicateur doit définir un membre qui a la valeur zéro afin que la valeur par défaut est une valeur valide de l’énumération. Le cas échéant, nommez le membre 'None'. Sinon, assignez la valeur zéro au membre plus fréquemment utilisé. Notez que, par défaut, si la valeur du premier membre d’énumération n’est pas définie dans la déclaration, sa valeur est zéro.

 Si une énumération qui a le <xref:System.FlagsAttribute> appliqué définit un membre de valeur zéro, son nom doit être 'None' pour indiquer qu’aucune valeur n’ont été définies dans l’énumération. À l’aide d’un membre de valeur zéro pour d’autres fins est contraire à l’utilisation de la <xref:System.FlagsAttribute> dans la mesure AND et ou opérateurs au niveau du bit sont inutiles avec le membre. Cela implique que seul un membre doit avoir la valeur zéro. Notez que si plusieurs membres qui ont la valeur zéro se produire dans une énumération attribuée par indicateurs, `Enum.ToString()` retourne des résultats incorrects pour les membres qui ne sont pas égales à zéro.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle pour les énumérations attribuée sans indicateur, définissez un membre qui a la valeur zéro ; Il s’agit d’une modification sans rupture. Pour les énumérations attribuées par indicateurs qui définissent un membre de valeur zéro, nommez ce membre 'None' et supprimer tous les membres qui ont une valeur égale à zéro ; Il s’agit d’une modification avec rupture.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle à l’exception des énumérations attribuées par indicateurs fournies précédemment.

## <a name="example"></a>Exemple
 L’exemple suivant montre deux énumérations qui satisfont la règle et une énumération, `BadTraceOptions`, qui enfreint la règle.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA2217 : Ne marquez pas les énumérations avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700 : Ne nommez pas les valeurs d’énumération 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712 : Ne préfixez pas les valeurs d’énumération avec le nom du type](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028 : Le stockage de l’énumération doit être Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027 : Marquez les énumérations avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Enum?displayProperty=fullName>



