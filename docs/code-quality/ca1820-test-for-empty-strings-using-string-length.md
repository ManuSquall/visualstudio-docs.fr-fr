---
title: 'CA1820 : Vérifiez la présence de chaînes vides par la longueur de chaîne'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: e290fa29f27638c327565825872e0de96bbd8bb7
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55483888"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820 : Vérifiez la présence de chaînes vides par la longueur de chaîne

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Category|Microsoft.Performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une chaîne est comparée à une chaîne vide à l’aide de <xref:System.Object.Equals%2A?displayProperty=nameWithType>.

## <a name="rule-description"></a>Description de la règle

Comparer des chaînes à l’aide de la <xref:System.String.Length%2A?displayProperty=nameWithType> propriété ou le <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> méthode est plus rapide que l’utilisation de <xref:System.Object.Equals%2A>. Il s’agit, car <xref:System.Object.Equals%2A> exécute des instructions MSIL très supérieur à soit <xref:System.String.IsNullOrEmpty%2A> ou le nombre d’instructions exécutées pour récupérer le <xref:System.String.Length%2A> propriété valeur et la comparer à zéro.

Pour les chaînes null, <xref:System.Object.Equals%2A> et <xref:System.String.Length%2A> == 0 se comportent différemment. Si vous essayez d’obtenir la valeur de la <xref:System.String.Length%2A> propriété sur une chaîne null, le common language runtime lève un <xref:System.NullReferenceException?displayProperty=fullName>. Si vous effectuez une comparaison entre une chaîne null et une chaîne vide, le common language runtime ne lève pas d’exception et retourne `false`. Test de valeur null n’affecte pas considérablement les performances relatives de ces deux approches. Lorsque vous ciblez .NET Framework 2.0 ou version ultérieure, utilisez le <xref:System.String.IsNullOrEmpty%2A> (méthode). Sinon, utilisez le <xref:System.String.Length%2A> == 0 comparaison autant que possible.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, modifiez la comparaison à utiliser le <xref:System.String.Length%2A> propriété et test pour la chaîne null. Si vous ciblez .NET Framework 2.0 ou version ultérieure, utilisez le <xref:System.String.IsNullOrEmpty%2A> (méthode).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle si les performances ne sont pas un problème.

## <a name="example"></a>Exemple

L’exemple suivant illustre les différentes techniques utilisées pour rechercher une chaîne vide.

[!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]