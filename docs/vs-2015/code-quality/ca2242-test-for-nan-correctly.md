---
title: 'CA2242 : test de NaN correctement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8433ac081a45e3dbab80ffcd6f96e6d1db914337
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672007"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242 : Effectuez correctement des tests NaN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une expression teste une valeur par rapport à <xref:System.Single.NaN?displayProperty=fullName> ou <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 <xref:System.Double.NaN?displayProperty=fullName>, qui représente les valeurs not-a-Number, lorsqu’une opération arithmétique est non définie. Toute expression qui teste l’égalité entre une valeur et <xref:System.Double.NaN?displayProperty=fullName> retourne toujours `false`. Toute expression qui teste l’inégalité entre une valeur et <xref:System.Double.NaN?displayProperty=fullName> retourne toujours `true`.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle et déterminer précisément si une valeur représente <xref:System.Double.NaN?displayProperty=fullName>, utilisez <xref:System.Single.IsNaN%2A?displayProperty=fullName> ou <xref:System.Double.IsNaN%2A?displayProperty=fullName> pour tester la valeur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre deux expressions qui testent de manière incorrecte une valeur par rapport à <xref:System.Double.NaN?displayProperty=fullName> et une expression qui utilise correctement <xref:System.Double.IsNaN%2A?displayProperty=fullName> pour tester la valeur.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]
