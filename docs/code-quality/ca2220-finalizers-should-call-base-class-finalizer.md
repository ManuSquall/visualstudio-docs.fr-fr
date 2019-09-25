---
title: 'CA2220 : Les finaliseurs doivent appeler le finaliseur de leur classe de base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5af6b7872f0fa05183334e6acd2bc4922f84990
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231159"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220 : Les finaliseurs doivent appeler le finaliseur de leur classe de base

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type qui substitue <xref:System.Object.Finalize%2A?displayProperty=fullName> n’appelle pas la <xref:System.Object.Finalize%2A> méthode dans sa classe de base.

## <a name="rule-description"></a>Description de la règle

La finalisation doit être propagée par le biais de la hiérarchie d'héritage. Pour garantir cela, les types doivent appeler leur méthode <xref:System.Object.Finalize%2A> de classe de base à <xref:System.Object.Finalize%2A> partir de leur propre méthode. Le C# compilateur ajoute automatiquement l’appel au finaliseur de la classe de base.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, appelez la méthode du <xref:System.Object.Finalize%2A> type de base à partir de votre <xref:System.Object.Finalize%2A> méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle. Certains compilateurs qui ciblent le common language runtime insèrent un appel au finaliseur du type de base dans le langage MSIL (Microsoft Intermediate Language). Si un avertissement de cette règle est signalé, votre compilateur n’insère pas l’appel et vous devez l’ajouter à votre code.

## <a name="example"></a>Exemple

L’exemple de Visual Basic suivant illustre un `TypeB` type qui appelle correctement <xref:System.Object.Finalize%2A> la méthode dans sa classe de base.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>Voir aussi

- [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)