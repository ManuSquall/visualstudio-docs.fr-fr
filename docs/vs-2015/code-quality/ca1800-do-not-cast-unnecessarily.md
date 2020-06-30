---
title: 'CA1800 : n’effectuez pas de cast inutilement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 757d66ef719b3a1f39a9164dfd50ce1fcf8799db
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547795"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800 : N'effectuez pas de cast inutilement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Category|Microsoft. performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode effectue des conversions en double sur l’un de ses arguments ou variables locales. Pour une analyse complète par cette règle, l’assembly testé doit être généré à l’aide des informations de débogage et le fichier de base de données du programme (. pdb) associé doit être disponible.

## <a name="rule-description"></a>Description de la règle
 Les casts en doublon font baisser les performances, surtout lorsque les casts sont exécutés au sein d'instructions d'itération compactes. Pour les opérations de cast en doublon explicites, stockez le résultat du cast dans une variable locale et utilisez la variable locale à la place des opérations de conversion en double.

 Si l' `is` opérateur C# est utilisé pour déterminer si le cast aboutit avant l’exécution du cast réel, envisagez de tester le résultat de l’opérateur à la `as` place. Cela fournit les mêmes fonctionnalités sans l’opération de conversion implicite effectuée par l' `is` opérateur.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez l’implémentation de la méthode afin de réduire le nombre d’opérations de conversion.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle, ou d’ignorer complètement la règle, si les performances ne sont pas un problème.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui enfreint la règle à l’aide de l' `is` opérateur C#. Une deuxième méthode remplit la règle en remplaçant l' `is` opérateur par un test par rapport au résultat de l' `as` opérateur, ce qui réduit le nombre d’opérations de conversion par itération de deux à un.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode, `start_Click` , qui a plusieurs casts explicites en double, qui violent la règle, et une méthode, `reset_Click` , qui satisfait la règle en stockant le cast dans une variable locale.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>Voir aussi
 [tel](https://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [is](https://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43) quel
