---
title: 'CA2215 : Méthodes Dispose doivent appeler dispose de la classe de base'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8531bfd8407415aa1868fb5e1f633be442ce9bc7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844221"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215 : Méthodes Dispose doivent appeler dispose de la classe de base

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Catégorie|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type qui implémente <xref:System.IDisposable?displayProperty=fullName> hérite d’un type qui implémente également <xref:System.IDisposable>. Le <xref:System.IDisposable.Dispose%2A> méthode du type héritant n’appelle pas la <xref:System.IDisposable.Dispose%2A> méthode du type parent.

## <a name="rule-description"></a>Description de la règle
 Si un type hérite d’un type JETABLE, il doit appeler la <xref:System.IDisposable.Dispose%2A> méthode du type de base à partir de son propre <xref:System.IDisposable.Dispose%2A> (méthode). Appel de la méthode de type de base Dispose garantit que toutes les ressources créées par le type de base sont publiées.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appelez `base`.<xref:System.IDisposable.Dispose%2A> dans votre <xref:System.IDisposable.Dispose%2A> (méthode).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si l’appel à `base`.<xref:System.IDisposable.Dispose%2A> se produit à un niveau plus profond appelant que la règle de contrôle.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type `TypeA` qui implémente <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type `TypeB` qui hérite du type `TypeA` et appelle correctement son <xref:System.IDisposable.Dispose%2A> (méthode).

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>Voir aussi

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)