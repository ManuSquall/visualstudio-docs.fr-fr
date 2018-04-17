---
title: 'CA2242 : Correctement des tests NaN | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a782c0b3f32c9733b47ded29852e006f8ba7c1aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242 : Effectuez correctement des tests NaN
|||  
|-|-|  
|TypeName|TestForNaNCorrectly|  
|CheckId|CA2242|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Une expression teste une valeur par rapport à <xref:System.Single.NaN?displayProperty=fullName> ou <xref:System.Double.NaN?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Description de la règle  
 <xref:System.Double.NaN?displayProperty=fullName>, qui représente le not-a-number, résulte lorsqu’une opération arithmétique est indéfinie. Toute expression qui teste l’égalité entre une valeur et <xref:System.Double.NaN?displayProperty=fullName> retourne toujours `false`. Toute expression qui teste l’inégalité entre une valeur et <xref:System.Double.NaN?displayProperty=fullName> retourne toujours `true`.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle et permettra de déterminer si une valeur représente <xref:System.Double.NaN?displayProperty=fullName>, utilisez <xref:System.Single.IsNaN%2A?displayProperty=fullName> ou <xref:System.Double.IsNaN%2A?displayProperty=fullName> pour tester la valeur.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre deux expressions qui testent de manière incorrecte une valeur par rapport à <xref:System.Double.NaN?displayProperty=fullName> et une expression qui utilise correctement <xref:System.Double.IsNaN%2A?displayProperty=fullName> pour tester la valeur.  
  
 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]