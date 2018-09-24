---
title: 'CA2220 : Les finaliseurs doivent appeler le finaliseur de leur classe de base'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c814324ac21017acf6a0182f7807b0a0878c8aca
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551205"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220 : Les finaliseurs doivent appeler le finaliseur de leur classe de base

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type qui substitue <xref:System.Object.Finalize%2A?displayProperty=fullName> n’appelle pas la <xref:System.Object.Finalize%2A> méthode dans sa classe de base.

## <a name="rule-description"></a>Description de la règle

La finalisation doit être propagée par le biais de la hiérarchie d'héritage. Pour ce faire, les types doivent appeler leur classe de base <xref:System.Object.Finalize%2A> méthode à partir de leurs propres <xref:System.Object.Finalize%2A> (méthode). Le compilateur c# ajoute automatiquement l’appel au finaliseur de la classe de base.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, appelez le type de base <xref:System.Object.Finalize%2A> méthode à partir de votre <xref:System.Object.Finalize%2A> (méthode).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle. Certains compilateurs qui ciblent le common language runtime insérer un appel à un finaliseur du type de base en langage intermédiaire Microsoft (MSIL). Si un avertissement de cette règle est signalé, votre compilateur n’insère pas de l’appel, et vous devez l’ajouter à votre code.

## <a name="example"></a>Exemple

L’exemple Visual Basic suivant illustre un type `TypeB` qui appelle correctement le <xref:System.Object.Finalize%2A> méthode dans sa classe de base.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>Voir aussi

- [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)