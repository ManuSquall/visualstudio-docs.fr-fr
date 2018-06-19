---
title: 'CA1023 : Les indexeurs ne doivent pas être multidimensionnels'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3864cbef5a5ba6c013d05112af46d641aa3c1634
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31895976"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023 : Les indexeurs ne doivent pas être multidimensionnels
|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé contient un indexeur public ou protégé qui utilise plusieurs index.

## <a name="rule-description"></a>Description de la règle
 Les indexeurs, c'est-à-dire les propriétés indexées, doivent utiliser un index unique. Les indexeurs multidimensionnels peuvent considérablement diminuer la facilité d’utilisation de la bibliothèque. Si le design nécessite plusieurs index, reconsidérez si le type représente une banque de données logique. Si ce n’est pas le cas, utilisez une méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez le design pour utiliser un entier unique ou un index de chaîne, ou utilisez une méthode au lieu de l’indexeur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle uniquement après avoir soigneusement la nécessité de l’indexeur non standard.

## <a name="example"></a>Exemple
 L’exemple suivant présente un type, `DayOfWeek03`, avec un indexeur multidimensionnel qui enfreint la règle. L’indexeur peut être considéré comme un type de conversion et par conséquent plus convenablement exposé comme une méthode. Le type est repensé dans `RedesignedDayOfWeek03` pour satisfaire la règle.

 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]

## <a name="related-rules"></a>Règles associées
 [CA1043 : Utiliser un argument entier ou chaîne pour les indexeurs](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024 : Utilisez des propriétés quand c’est approprié](../code-quality/ca1024-use-properties-where-appropriate.md)