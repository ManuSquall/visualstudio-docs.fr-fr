---
title: 'CA1820 : tester les chaînes vides à l’aide de la longueur de chaîne | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 296eb6407e3ce63b0eb28ff86c215c12ec724ce9
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545312"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820 : Vérifiez la présence de chaînes vides par la longueur de chaîne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Category|Microsoft. performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une chaîne est comparée à la chaîne vide à l’aide de <xref:System.Object.Equals%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Description de la règle
 La comparaison de chaînes à l’aide de la <xref:System.String.Length%2A?displayProperty=fullName> propriété ou de la <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> méthode est beaucoup plus rapide que l’utilisation de <xref:System.Object.Equals%2A> . Cela est dû au fait que <xref:System.Object.Equals%2A> exécute beaucoup plus d’instructions MSIL que <xref:System.String.IsNullOrEmpty%2A> ou le nombre d’instructions exécutées pour récupérer la valeur de la <xref:System.String.Length%2A> propriété et la comparer à zéro.

 Vous devez savoir que <xref:System.Object.Equals%2A> et <xref:System.String.Length%2A> = = 0 se comporte différemment pour les chaînes NULL. Si vous essayez d’obtenir la valeur de la <xref:System.String.Length%2A> propriété sur une chaîne NULL, le Common Language Runtime lève une <xref:System.NullReferenceException?displayProperty=fullName> . Si vous effectuez une comparaison entre une chaîne NULL et la chaîne vide, le common language runtime ne lève pas d’exception ; la comparaison retourne `false` . Le test de la valeur NULL n’affecte pas de manière significative les performances relatives de ces deux approches. Quand vous ciblez [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , utilisez la <xref:System.String.IsNullOrEmpty%2A> méthode. Sinon, utilisez la <xref:System.String.Length%2A> comparaison = = dans la mesure du possible.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez la comparaison afin d’utiliser la <xref:System.String.Length%2A> propriété et de tester la chaîne NULL. Si vous ciblez [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , utilisez la <xref:System.String.IsNullOrEmpty%2A> méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si les performances ne sont pas un problème.

## <a name="example"></a>Exemple
 L’exemple suivant illustre les différentes techniques utilisées pour rechercher une chaîne vide.

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]
