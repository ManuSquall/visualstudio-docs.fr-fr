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
ms.openlocfilehash: 5d9139314d52c4c50de84a45f227e6df5715bf02
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540658"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220 : Les finaliseurs doivent appeler le finaliseur de leur classe de base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type qui substitue <xref:System.Object.Finalize%2A?displayProperty=fullName> n’appelle pas la <xref:System.Object.Finalize%2A> méthode dans sa classe de base.

## <a name="rule-description"></a>Description de la règle
 La finalisation doit être propagée par le biais de la hiérarchie d'héritage. Pour garantir cela, les types doivent appeler leur <xref:System.Object.Finalize%2A> méthode de classe de base à partir de leur propre <xref:System.Object.Finalize%2A> méthode. Le compilateur C# ajoute automatiquement l’appel au finaliseur de la classe de base.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appelez la méthode du type <xref:System.Object.Finalize%2A> de base à partir de votre <xref:System.Object.Finalize%2A> méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Certains compilateurs qui ciblent le common language runtime insèrent un appel au finaliseur du type de base dans le langage MSIL (Microsoft Intermediate Language). Si un avertissement de cette règle est signalé, votre compilateur n’insère pas l’appel et vous devez l’ajouter à votre code.

## <a name="example"></a>Exemple
 L’exemple de Visual Basic suivant illustre un type `TypeB` qui appelle correctement la <xref:System.Object.Finalize%2A> méthode dans sa classe de base.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Voir aussi
 [Dispose, modèle](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
