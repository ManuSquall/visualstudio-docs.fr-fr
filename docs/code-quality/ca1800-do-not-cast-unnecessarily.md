---
title: 'CA1800 : N’effectuez pas de cast inutilement'
ms.date: 10/26/2017
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 1ef6e73812a63fdc4cc4392621ab49b279a32d18
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822027"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800 : N’effectuez pas de cast inutilement

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Category|Microsoft.Performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Une méthode effectue des casts en double sur un de ses arguments ou les variables locales.

Pour l’analyse complète par cette règle, l’assembly testé doit être construit à l’aide des informations de débogage et le fichier de base de données (.pdb) du programme associé doit être disponible.

## <a name="rule-description"></a>Description de la règle
Les casts en doublon font baisser les performances, surtout lorsque les casts sont exécutés au sein d'instructions d'itération compactes. Pour les opérations de casts en doublon explicites, stocker le résultat du cast dans une variable locale et utilisez la variable locale au lieu des opérations de cast en double.

Si C# `is` opérateur est utilisé pour déterminer si le cast va réussir avant l’exécution proprement dite, envisagez de tester le résultat de la `as` opérateur à la place. Cela fournit les mêmes fonctionnalités sans l’opération de cast implicite est effectuée par le `is` opérateur. Ou, dans c# 7.0 et versions ultérieures, utilisez le `is` opérateur avec [critères spéciaux](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) de vérifier la conversion de type et de convertir l’expression à une variable de ce type en une seule étape.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez l’implémentation de méthode pour réduire le nombre d’opérations de cast.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est recommandé de supprimer un avertissement de cette règle, ou à ignorer la règle, si les performances ne sont pas un problème.

## <a name="examples"></a>Exemples
 L’exemple suivant montre une méthode qui viole la règle à l’aide de C# `is` opérateur. Une deuxième méthode satisfait la règle en remplaçant le `is` opérateur avec un test par rapport au résultat de la `as` opérateur, ce qui réduit le nombre d’opérations de cast par itération de deux à un. Une troisième méthode satisfait également à la règle à l’aide de `is` avec [critères spéciaux](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) pour créer une variable du type souhaité si la conversion de type réussirait.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

 L’exemple suivant montre une méthode, `start_Click`, qui a plusieurs conversions explicites en double, ce qui viole la règle et une méthode, `reset_Click`, ce qui satisfait la règle en stockant le cast dans une variable locale.

 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>Voir aussi

- [as (référence c#)](/dotnet/csharp/language-reference/keywords/as)
- [is (référence c#)](/dotnet/csharp/language-reference/keywords/is)