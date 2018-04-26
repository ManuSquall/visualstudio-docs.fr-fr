---
title: 'CA1816 : Appeler GC.SuppressFinalize correctement'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3c3b7a7dd5e7c9ed8e5b713578dd682384dbf30
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816 : Appeler GC.SuppressFinalize correctement
|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Category|Microsoft. Utilisation|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

-   Une méthode qui est une implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> n’appelle pas <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

-   Une méthode qui n’est pas une implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> appelle <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

-   Une méthode appelle <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> et passe un élément autre que celui-ci (Me en Visual Basic).

## <a name="rule-description"></a>Description de la règle
 Le <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> méthode permet aux utilisateurs de libérer des ressources à tout moment avant l’objet devienne disponible pour le garbage collection. Si la <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> est appelée, elle libère les ressources de l’objet. Cela rend la finalisation inutile. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> doit appeler <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> pour le garbage collector n’appelle pas le finaliseur de l’objet.

 Pour empêcher les types dérivés avec finaliseurs réimplémenter <xref:System.IDisposable> et pour l’appeler, des types unsealed sans les finaliseurs doivent toujours appeler <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle :

 Si la méthode est une implémentation de <xref:System.IDisposable.Dispose%2A>, ajoutez un appel à <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 Si la méthode n’est pas une implémentation de <xref:System.IDisposable.Dispose%2A>, supprimez l’appel à <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> ou déplacez-le vers le type <xref:System.IDisposable.Dispose%2A> implémentation.

 Modifiez tous les appels à <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> à passer à celui-ci (Me en Visual Basic).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez uniquement un avertissement de cette règle si vous utilisez délibérément <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> pour contrôler la durée de vie d’autres objets. Ne supprimez aucun avertissement de cette règle si une implémentation de <xref:System.IDisposable.Dispose%2A> n’appelle pas <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>. Dans ce cas, le basculement supprimer la finalisation dégrade les performances et n’apporte aucun avantage.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui incorrectement appels <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui correctement les appels <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>Règles associées
 [CA2215 : Les méthodes Dispose doivent appeler la méthode Dispose de la classe de base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216 : Les types supprimables doivent déclarer un finaliseur](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Voir aussi
 [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)