---
title: "CA2242&#160;: Effectuez correctement des tests NaN | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TestForNaNCorrectly"
  - "CA2242"
helpviewer_keywords: 
  - "CA2242"
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2242&#160;: Effectuez correctement des tests NaN
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TestForNaNCorrectly|  
|CheckId|CA2242|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une expression teste une valeur par rapport à <xref:System.Single.Nan?displayProperty=fullName> ou à <xref:System.Double.Nan?displayProperty=fullName>.  
  
## Description de la règle  
 <xref:System.Double.NaN?displayProperty=fullName> qui représente une valeur non numérique, résulte lorsqu'une opération arithmétique est indéfinie.  Une expression qui teste l'égalité entre une valeur et <xref:System.Double.NaN?displayProperty=fullName> retourne toujours `false`.  Une expression qui teste l'inégalité entre une valeur et <xref:System.Double.NaN?displayProperty=fullName> retourne toujours `true`.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle et déterminer correctement si une valeur représente <xref:System.Double.NaN?displayProperty=fullName>, utilisez <xref:System.Single.IsNan%2A?displayProperty=fullName> ou <xref:System.Double.IsNan%2A?displayProperty=fullName> pour tester la valeur.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant indique deux expressions qui testent de manière incorrecte une valeur par rapport à <xref:System.Double.NaN?displayProperty=fullName> et une expression qui utilise correctement <xref:System.Double.IsNaN%2A?displayProperty=fullName> pour tester la valeur.  
  
 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-cs[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]