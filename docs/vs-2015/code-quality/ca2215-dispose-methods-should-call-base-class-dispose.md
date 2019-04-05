---
title: 'CA2215 : Méthodes Dispose doivent appeler dispose de la classe de base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fb0fb1e1270e2e881b885873cf202cdf38106a05
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950612"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215 : Les méthodes Dispose doivent appeler la méthode Dispose de la classe de base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Category|Microsoft.Usage|
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

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type `TypeB` qui hérite du type `TypeA` et appelle correctement son <xref:System.IDisposable.Dispose%2A> (méthode).

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.IDisposable?displayProperty=fullName> [Modèle de suppression](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
