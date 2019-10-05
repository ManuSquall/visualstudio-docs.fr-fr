---
title: 'CA2215 : Les méthodes Dispose doivent appeler la méthode Dispose de la classe de base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 468b63ca554ea126bbd621a2502e54540e6ed068
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231279"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215 : Les méthodes Dispose doivent appeler la méthode Dispose de la classe de base

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Un type qui implémente <xref:System.IDisposable?displayProperty=fullName> hérite d’un type qui <xref:System.IDisposable>implémente également. La <xref:System.IDisposable.Dispose%2A> méthode du type qui hérite n’appelle pas la <xref:System.IDisposable.Dispose%2A> méthode du type parent.

## <a name="rule-description"></a>Description de la règle
Si un type hérite d’un type supprimable, il doit appeler <xref:System.IDisposable.Dispose%2A> la méthode du type de base à partir de <xref:System.IDisposable.Dispose%2A> sa propre méthode. L’appel de la méthode de type de base dispose garantit que toutes les ressources créées par le type de base sont libérées.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, appelez `base`.<xref:System.IDisposable.Dispose%2A> dans votre <xref:System.IDisposable.Dispose%2A> méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle si l' `base`appel à.<xref:System.IDisposable.Dispose%2A> se produit à un niveau d’appel plus profond que la règle vérifie.

## <a name="example"></a>Exemple
L’exemple suivant illustre un type `TypeA` qui <xref:System.IDisposable>implémente.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>Exemple
L’exemple suivant montre un type `TypeB` qui hérite du type `TypeA` et appelle correctement sa <xref:System.IDisposable.Dispose%2A> méthode.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>Voir aussi

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)