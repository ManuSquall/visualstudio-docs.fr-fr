---
title: 'CA2242 : Effectuez correctement des tests NaN'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0e74ec49667a4fe66c399bd15e8b24aa6589ce88
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237839"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242 : Effectuez correctement des tests NaN

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Une expression teste une valeur <xref:System.Single.NaN?displayProperty=fullName> par <xref:System.Double.NaN?displayProperty=fullName>rapport à ou.

## <a name="rule-description"></a>Description de la règle
 <xref:System.Double.NaN?displayProperty=fullName>, qui représente les résultats not-a-Number, lorsqu’une opération arithmétique est non définie. Toute expression qui teste l’égalité entre une <xref:System.Double.NaN?displayProperty=fullName> valeur et `false`retourne toujours. Toute expression qui teste l’inégalité entre une <xref:System.Double.NaN?displayProperty=fullName> valeur et `true`retourne toujours.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle et déterminer avec précision si une valeur représente <xref:System.Double.NaN?displayProperty=fullName>, utilisez <xref:System.Single.IsNaN%2A?displayProperty=fullName> ou <xref:System.Double.IsNaN%2A?displayProperty=fullName> pour tester la valeur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
L’exemple suivant montre deux expressions qui testent de manière incorrecte <xref:System.Double.NaN?displayProperty=fullName> une valeur par rapport à une <xref:System.Double.IsNaN%2A?displayProperty=fullName> expression qui utilise correctement pour tester la valeur.

[!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
[!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]