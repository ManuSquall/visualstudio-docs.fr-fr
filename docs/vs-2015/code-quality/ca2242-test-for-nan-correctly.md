---
title: 'CA2242 : effectuez Des tests NaN correctement | Microsoft Docs'
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
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d04ac9152ef1b60a6d546ed94713bc267584ae36
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236494"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242 : Effectuez correctement des tests NaN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]



