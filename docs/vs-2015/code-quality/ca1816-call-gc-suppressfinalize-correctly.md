---
title: 'CA1816 : appelez GC. SuppressFinalize correctement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: acc86c278faa877897d294e72632762eff834a76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668387"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816 : Appeler GC.SuppressFinalize correctement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Category|Librairie. Utilisation|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

- Une méthode qui est une implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> n’appelle pas <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

- Une méthode qui n’est pas une implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> appelle <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

- Une méthode appelle <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> et transmet autre chose que this (me dans Visual Basic).

## <a name="rule-description"></a>Description de la règle
 La méthode <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> permet aux utilisateurs de libérer des ressources à tout moment avant que l’objet ne devienne disponible pour les garbage collection. Si la méthode <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> est appelée, elle libère les ressources de l’objet. La finalisation n’est donc pas nécessaire. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> doit appeler <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> afin que le garbage collector n’appelle pas le finaliseur de l’objet.

 Pour empêcher les types dérivés avec finaliseurs d’avoir à réimplémenter [System. IDisposable] (<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) et pour l’appeler, les types non scellés sans finaliseurs doivent toujours appeler <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle :

 Si la méthode est une implémentation de <xref:System.IDisposable.Dispose%2A>, ajoutez un appel à <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 Si la méthode n’est pas une implémentation de <xref:System.IDisposable.Dispose%2A>, supprimez l’appel à <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> ou déplacez-le vers l’implémentation <xref:System.IDisposable.Dispose%2A> du type.

 Remplacez tous les appels à <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> pour les transmettre (moi en Visual Basic).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle uniquement si vous délibéréz l’utilisation de <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> pour contrôler la durée de vie des autres objets. Ne supprimez pas un avertissement de cette règle si une implémentation de <xref:System.IDisposable.Dispose%2A> n’appelle pas <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>. Dans ce cas, le fait de ne pas supprimer la finalisation dégrade les performances et ne fournit aucun avantage.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui appelle incorrectement <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui appelle correctement <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA2215 : Les méthodes Dispose doivent appeler la méthode Dispose de la classe de base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216 : Les types supprimables doivent déclarer un finaliseur](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Voir aussi
 [Dispose, modèle](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
