---
title: 'CA1816 : Appeler GC.SuppressFinalize correctement'
ms.date: 06/30/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: d8f7952758c091765116f44ef4454cd9214e0b49
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940445"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816 : Appeler GC.SuppressFinalize correctement

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Category|Microsoft. Utilisation|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Les violations de cette règle peuvent être dû :

- Une méthode qui est une implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> et n’appelle pas <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Une méthode qui n’est pas une implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> et appelle <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Une méthode qui appelle <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> et passe un élément autre que [this (c#)](/dotnet/csharp/language-reference/keywords/this) ou [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="rule-description"></a>Description de la règle

Le <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> méthode permet aux utilisateurs de libérer des ressources à tout moment avant l’objet devienne disponible pour le garbage collection. Si le <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> est appelée, elle libère les ressources de l’objet. Cela rend la finalisation inutile. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> doit appeler <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> afin du garbage collector n’appelle pas le finaliseur de l’objet.

Pour empêcher les types dérivés avec finaliseurs d’avoir à implémenter de nouveau <xref:System.IDisposable> et pour l’appeler, les types unsealed sans les finaliseurs doivent toujours appeler <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle :

- Si la méthode est une implémentation de <xref:System.IDisposable.Dispose%2A>, ajoutez un appel à <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Si la méthode n’est pas une implémentation de <xref:System.IDisposable.Dispose%2A>, supprimez l’appel à <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> ou déplacez-le vers le type <xref:System.IDisposable.Dispose%2A> implémentation.

- Modifier tous les appels à <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> à passer [this (c#)](/dotnet/csharp/language-reference/keywords/this) ou [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Supprimez uniquement un avertissement de cette règle si vous utilisez délibérément <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> pour contrôler la durée de vie d’autres objets. Ne pas supprimer un avertissement de cette règle si une implémentation de <xref:System.IDisposable.Dispose%2A> n’appelle pas <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>. Dans ce cas, ne parvient pas à supprimer la finalisation dégrade les performances et ne présente aucun avantage.

## <a name="example-that-violates-ca1816"></a>Exemple qui enfreint CA1816

Ce code montre une méthode qui appelle <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>, mais ne remplit pas [this (c#)](/dotnet/csharp/language-reference/keywords/this) ou [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me). Par conséquent, ce code enfreint la règle CA1816.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>Exemple répondant CA1816

Cet exemple montre une méthode qui correctement appels <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> en passant [this (c#)](/dotnet/csharp/language-reference/keywords/this) ou [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>Règles associées

- [CA2215 : Méthodes Dispose doivent appeler dispose de la classe de base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216 : Les types supprimables doivent déclarer un finaliseur](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Voir aussi

- [Modèle de suppression](/dotnet/standard/design-guidelines/dispose-pattern)