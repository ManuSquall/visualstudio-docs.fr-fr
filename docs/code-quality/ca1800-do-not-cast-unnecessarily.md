---
title: "CA1800 : N'effectuez pas de cast inutilement"
ms.date: 10/26/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: 34c03adb8ff34d3590ed93264d77536c4cdff080
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915567"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800 : N'effectuez pas de cast inutilement
|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Category|Microsoft.Performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Une méthode exécute des casts en doublon sur l’un de ses arguments ou les variables locales.

Pour l’analyse complète par cette règle, l’assembly testé doit être construit à l’aide des informations de débogage et le fichier de base de données (.pdb) de programme associé doit être disponible.

## <a name="rule-description"></a>Description de la règle
Les casts en doublon font baisser les performances, surtout lorsque les casts sont exécutés au sein d'instructions d'itération compactes. Pour les opérations de casts en doublon explicites, enregistre le résultat de la conversion en dans une variable locale et utilisez la variable locale à la place les opérations de casts en doublon.

Si c# `is` opérateur est utilisé pour tester si le cast va réussir avant l’exécution proprement dite, testez le résultat de la `as` opérateur à la place. Cette fonctionnalité est la même sans l’opération de cast implicite est effectuée par le `is` opérateur. Ou, dans c# 7.0 et versions ultérieures, utilisez la `is` opérateur avec [recherche de correspondance](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) de vérifier la conversion de type et de convertir l’expression à une variable de ce type en une seule étape.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez l’implémentation de méthode pour réduire le nombre d’opérations de cast.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle, ou pour ignorer la règle, si les performances ne sont pas un problème.

## <a name="examples"></a>Exemples
 L’exemple suivant montre une méthode qui enfreint la règle à l’aide du langage c# `is` opérateur. Une deuxième méthode satisfait la règle en remplaçant le `is` opérateur avec un test par rapport au résultat de la `as` (opérateur), ce qui réduit le nombre d’opérations de cast par itération de deux à un. Une troisième méthode également satisfait à la règle à l’aide de `is` avec [recherche de correspondance](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) pour créer une variable du type souhaité si la conversion de type réussit.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

 L’exemple suivant montre une méthode, `start_Click`, qui a plusieurs conversions explicites en double, ce qui enfreint la règle et une méthode, `reset_Click`, qui satisfait la règle en stockant le cast dans une variable locale.

 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>Voir aussi
[en tant que (référence c#)](/dotnet/csharp/language-reference/keywords/as)
[est (référence c#)](/dotnet/csharp/language-reference/keywords/is)