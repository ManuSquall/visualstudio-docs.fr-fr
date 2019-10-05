---
title: 'CA1820 : Vérifiez la présence de chaînes vides par la longueur de chaîne'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b197cacc764f1f5472d3eb074ac89199db508408
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233430"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820 : Vérifiez la présence de chaînes vides par la longueur de chaîne

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Category|Microsoft. performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une chaîne est comparée à la chaîne vide à <xref:System.Object.Equals%2A?displayProperty=nameWithType>l’aide de.

## <a name="rule-description"></a>Description de la règle

La comparaison de chaînes <xref:System.String.Length%2A?displayProperty=nameWithType> à l’aide <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> de la propriété ou de <xref:System.Object.Equals%2A>la méthode est plus rapide que l’utilisation de. Cela est dû <xref:System.Object.Equals%2A> au fait que exécute beaucoup plus d’instructions <xref:System.String.IsNullOrEmpty%2A> MSIL que ou le nombre d’instructions exécutées <xref:System.String.Length%2A> pour récupérer la valeur de la propriété et la comparer à zéro.

Pour les chaînes null <xref:System.Object.Equals%2A> , `<string>.Length == 0` et se comportent différemment. Si vous essayez d’obtenir la valeur de la <xref:System.String.Length%2A> propriété sur une chaîne NULL, le Common Language Runtime lève une. <xref:System.NullReferenceException?displayProperty=fullName> Si vous effectuez une comparaison entre une chaîne NULL et la chaîne vide, la common language runtime ne lève pas d’exception et retourne `false`. Le test de la valeur NULL n’affecte pas de manière significative les performances relatives de ces deux approches. Quand vous ciblez .NET Framework 2,0 ou une version <xref:System.String.IsNullOrEmpty%2A> ultérieure, utilisez la méthode. Dans le cas contraire <xref:System.String.Length%2A> , utilisez la comparaison = = 0 dans la mesure du possible.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, modifiez la comparaison pour utiliser la <xref:System.String.IsNullOrEmpty%2A> méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle si les performances ne sont pas un problème.

## <a name="example"></a>Exemple

L’exemple suivant illustre les différentes techniques utilisées pour rechercher une chaîne vide.

[!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]