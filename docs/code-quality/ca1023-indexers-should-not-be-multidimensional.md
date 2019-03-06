---
title: 'CA1023 : Les indexeurs ne doivent pas être multidimensionnels'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ef3afd9dda70d02698abec5459b36e6acc2c5ed0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55924543"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023 : Les indexeurs ne doivent pas être multidimensionnels

|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé contient un indexeur public ou protégé qui utilise plusieurs index.

## <a name="rule-description"></a>Description de la règle
 Les indexeurs, autrement dit, les propriétés indexées, doivent utiliser un index unique. Les indexeurs multidimensionnels peuvent réduire considérablement la facilité d’utilisation de la bibliothèque. Si la conception nécessite plusieurs index, reconsidérez si le type représente un magasin de données logique. Si ce n’est pas le cas, utilisez une méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez le design pour utiliser un entier solitaire ou un index de chaîne, ou utilisez une méthode au lieu de l’indexeur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimer un avertissement de cette règle uniquement après avoir soigneusement envisagé la nécessité de l’indexeur non standard.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type, `DayOfWeek03`, avec un indexeur multidimensionnel qui viole la règle. L’indexeur peut être considéré comme un type de conversion et par conséquent plus convenablement exposé comme une méthode. Le type est repensé dans `RedesignedDayOfWeek03` pour satisfaire la règle.

 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]

## <a name="related-rules"></a>Règles associées
 [CA1043 : Utilisez l’argument de chaîne ou intégral pour les indexeurs](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024 : Utiliser des propriétés lorsque nécessaire](../code-quality/ca1024-use-properties-where-appropriate.md)