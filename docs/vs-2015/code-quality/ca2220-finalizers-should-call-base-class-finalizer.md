---
title: 'Ca2220/85 : les finaliseurs doivent appeler le finaliseur de la classe de base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1a4538c66d351956da8168d4f84c1895190ab453
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663586"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220 : Les finaliseurs doivent appeler le finaliseur de leur classe de base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Type qui substitue <xref:System.Object.Finalize%2A?displayProperty=fullName> n’appelle pas la méthode <xref:System.Object.Finalize%2A> dans sa classe de base.

## <a name="rule-description"></a>Description de la règle
 La finalisation doit être propagée par le biais de la hiérarchie d'héritage. Pour ce faire, les types doivent appeler leur classe de base <xref:System.Object.Finalize%2A> méthode à partir de leur propre méthode <xref:System.Object.Finalize%2A>. Le C# compilateur ajoute automatiquement l’appel au finaliseur de la classe de base.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appelez la méthode <xref:System.Object.Finalize%2A> du type de base à partir de votre méthode <xref:System.Object.Finalize%2A>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Certains compilateurs qui ciblent le common language runtime insèrent un appel au finaliseur du type de base dans le langage MSIL (Microsoft Intermediate Language). Si un avertissement de cette règle est signalé, votre compilateur n’insère pas l’appel et vous devez l’ajouter à votre code.

## <a name="example"></a>Exemple
 L’exemple de Visual Basic suivant montre un type `TypeB` qui appelle correctement la méthode <xref:System.Object.Finalize%2A> dans sa classe de base.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Voir aussi
 [Dispose, modèle](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
