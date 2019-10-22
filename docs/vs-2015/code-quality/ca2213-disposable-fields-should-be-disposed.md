---
title: 'CA2213 : les champs supprimables doivent être supprimés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8ebeae3e5e367bb2c1a09bc1cb38dcc80d2c3826
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662896"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213 : Les champs pouvant être supprimés doivent l'être
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type qui implémente <xref:System.IDisposable?displayProperty=fullName> déclare des champs de types qui implémentent également <xref:System.IDisposable>. La méthode <xref:System.IDisposable.Dispose%2A> du champ n’est pas appelée par la méthode <xref:System.IDisposable.Dispose%2A> du type déclarant.

## <a name="rule-description"></a>Description de la règle
 Un type est responsable de la suppression de toutes ses ressources non managées. pour ce faire, implémentez <xref:System.IDisposable>. Cette règle vérifie si un type supprimable `T` déclare un champ `F` qui est une instance d’un type supprimable `FT`. Pour chaque `F` de champ, la règle tente de localiser un appel à `FT.Dispose`. La règle recherche les méthodes appelées par `T.Dispose` et un niveau plus bas (les méthodes appelées par les méthodes appelées par `FT.Dispose`).

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appelez <xref:System.IDisposable.Dispose%2A> sur les champs qui sont des types qui implémentent <xref:System.IDisposable> si vous êtes chargé d’allouer et de libérer les ressources non managées détenues par le champ.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si vous n’êtes pas responsable de la libération de la ressource détenue par le champ, ou si l’appel à <xref:System.IDisposable.Dispose%2A> se produit à un niveau d’appel plus profond que la vérification de la règle.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type `TypeA` qui implémente <xref:System.IDisposable> (`FT` dans la discussion précédente).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Exemple
 L’exemple suivant montre un type `TypeB` qui enfreint cette règle en déclarant un champ `aFieldOfADisposableType` (`F` dans la discussion précédente) comme un type supprimable (`TypeA`) et n’appelant pas <xref:System.IDisposable.Dispose%2A> sur le champ. `TypeB` correspond à `T` dans la discussion précédente.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.IDisposable?displayProperty=fullName> [modèle de suppression](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
