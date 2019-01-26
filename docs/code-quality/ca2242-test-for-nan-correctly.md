---
title: 'CA2242 : Effectuez correctement des tests NaN'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 671febac88142159b89f0888dead24605cbc0caa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54991747"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242 : Effectuez correctement des tests NaN

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une expression teste une valeur par rapport à <xref:System.Single.NaN?displayProperty=fullName> ou <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 <xref:System.Double.NaN?displayProperty=fullName>, qui représente le not-a-number, se produit lorsque l’opération arithmétique n’est pas définie. Toute expression qui teste l’égalité entre une valeur et <xref:System.Double.NaN?displayProperty=fullName> retourne toujours `false`. Toute expression qui teste l’inégalité entre une valeur et <xref:System.Double.NaN?displayProperty=fullName> retourne toujours `true`.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle et de déterminer avec précision si une valeur représente <xref:System.Double.NaN?displayProperty=fullName>, utilisez <xref:System.Single.IsNaN%2A?displayProperty=fullName> ou <xref:System.Double.IsNaN%2A?displayProperty=fullName> pour tester la valeur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre deux expressions qui testent de manière incorrecte une valeur par rapport à <xref:System.Double.NaN?displayProperty=fullName> et une expression qui utilise correctement <xref:System.Double.IsNaN%2A?displayProperty=fullName> pour tester la valeur.

 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]