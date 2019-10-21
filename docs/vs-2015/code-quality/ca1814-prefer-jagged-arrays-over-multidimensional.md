---
title: 'CA1814 : préférer les tableaux en escalier à des tableaux multidimensionnels | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f0ac183321bd2a3070b1f1ddc54402b74c8fb823
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668419"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814 : Utilisez des tableaux en escalier à la place de tableaux multidimensionnels
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PreferJaggedArraysOverMultidimensional|
|CheckId|CA1814|
|Category|Microsoft. performance|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un membre est déclaré en tant que tableau multidimensionnel.

## <a name="rule-description"></a>Description de la règle
 Un tableau en escalier est un tableau dont les éléments sont des tableaux. Les tableaux qui composent les éléments peuvent être de différentes tailles, ce qui conduit à un gaspillage d'espace plus restreint pour certains groupes de données.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez le tableau multidimensionnel par un tableau en escalier.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle si le tableau multidimensionnel ne gaspille pas d’espace.

## <a name="example"></a>Exemple
 L’exemple suivant montre des déclarations pour les tableaux en escalier et multidimensionnels.

 [!code-csharp[FxCop.Performance.JaggedArrays#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/cs/FxCop.Performance.JaggedArrays.cs#1)]
 [!code-vb[FxCop.Performance.JaggedArrays#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/vb/FxCop.Performance.JaggedArrays.vb#1)]
