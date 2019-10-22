---
title: 'CA1023 : les indexeurs ne doivent pas être multidimensionnels | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1b7c4c82add8644a1c2c213536c2ad3c0097c3a6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661991"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023 : Les indexeurs ne doivent pas être multidimensionnels
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé contient un indexeur public ou protected qui utilise plus d’un index.

## <a name="rule-description"></a>Description de la règle
 Les indexeurs, c’est-à-dire les propriétés indexées, doivent utiliser un seul index. Les indexeurs multidimensionnels peuvent réduire considérablement l’utilisation de la bibliothèque. Si la conception requiert plusieurs index, reconsidérez si le type représente un magasin de données logiques. Si ce n’est pas le cas, utilisez une méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez la conception pour utiliser un entier ou un index de chaîne solitaire, ou utilisez une méthode au lieu de l’indexeur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle uniquement après avoir soigneusement envisagé la nécessité de l’indexeur non standard.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type, `DayOfWeek03`, avec un indexeur multidimensionnel qui enfreint la règle. L’indexeur peut être considéré comme un type de conversion et, par conséquent, est exposé de manière plus appropriée en tant que méthode. Le type est repensé dans `RedesignedDayOfWeek03` pour satisfaire la règle.

 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cpp/FxCop.Design.OneDimensionForIndexer.cpp#1)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cs/FxCop.Design.OneDimensionForIndexer.cs#1)]
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/vb/FxCop.Design.OneDimensionForIndexer.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1043 : Utiliser un argument entier ou chaîne pour les indexeurs](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024 : Utilisez des propriétés quand c’est approprié](../code-quality/ca1024-use-properties-where-appropriate.md)
