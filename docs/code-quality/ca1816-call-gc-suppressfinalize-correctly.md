---
title: 'CA1816 : Appeler GC.SuppressFinalize correctement'
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3fdd20df37586e50b5236872f1d84de48d08c87a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233527"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816 : Appeler GC.SuppressFinalize correctement

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Category|Librairie. Utilisation|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Les violations de cette règle peuvent être provoquées par :

- Méthode qui est une implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> et qui n’appelle <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>pas.

- Une méthode qui n’est pas une implémentation <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> de et <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>appelle.

- Méthode qui appelle <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> et transmet autre chose que [This (C#)](/dotnet/csharp/language-reference/keywords/this) ou [me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="rule-description"></a>Description de la règle

La <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> méthode permet aux utilisateurs de libérer des ressources à tout moment avant que l’objet devienne disponible pour garbage collection. Si la <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> méthode est appelée, elle libère les ressources de l’objet. La finalisation n’est donc pas nécessaire. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>doit appeler <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> afin que le garbage collector n’appelle pas le finaliseur de l’objet.

Pour empêcher que les types dérivés avec finaliseurs n’aient <xref:System.IDisposable> à réimplémenter et à l’appeler, les types non scellés sans <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>finaliseurs doivent toujours appeler.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle :

- Si la méthode est une implémentation de <xref:System.IDisposable.Dispose%2A>, ajoutez un appel à <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Si la méthode n’est pas une implémentation <xref:System.IDisposable.Dispose%2A>de, supprimez l’appel <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> à ou déplacez-le vers l' <xref:System.IDisposable.Dispose%2A> implémentation du type.

- Remplacez tous les appels <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> à pour passer [ThisC#()](/dotnet/csharp/language-reference/keywords/this) ou [me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Supprimez un avertissement de cette règle uniquement si vous utilisez <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> délibérément pour contrôler la durée de vie des autres objets. Ne supprimez pas d’avertissement de cette règle si une <xref:System.IDisposable.Dispose%2A> implémentation de <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>n’appelle pas. Dans ce cas, le fait de ne pas supprimer la finalisation dégrade les performances et n’offre aucun avantage.

## <a name="example-that-violates-ca1816"></a>Exemple qui enfreint CA1816

Ce code montre une méthode qui appelle <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>, mais ne passe pas [ThisC#()](/dotnet/csharp/language-reference/keywords/this) ou [me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me). Par conséquent, ce code ne respecte pas la règle CA1816.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>Exemple qui satisfait CA1816

Cet exemple montre une méthode qui appelle <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> correctement en passant [This (C#)](/dotnet/csharp/language-reference/keywords/this) ou [me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>Règles associées

- [CA2215 Les méthodes dispose doivent appeler la méthode dispose de la classe de base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216 Les types jetables doivent déclarer un finaliseur](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Voir aussi

- [Modèle de suppression](/dotnet/standard/design-guidelines/dispose-pattern)