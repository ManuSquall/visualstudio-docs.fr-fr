---
title: 'CA2230 : Utilisez le mot clé params pour les arguments de variables'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db6c66e65ed89e53d0cbbed671004c88bdbaed95
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982973"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230 : Utilisez le mot clé params pour les arguments de variables

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Category|Microsoft.Usage|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé contient une méthode publique ou protégée qui utilise le `VarArgs` convention d’appel.

## <a name="rule-description"></a>Description de la règle
 Le `VarArgs` convention d’appel est utilisée avec certaines définitions de méthode qui acceptent un nombre variable de paramètres. Une méthode à l’aide de la `VarArgs` convention d’appel n’est pas Common Language Specification (CLS) conforme et ne peut pas être accessible entre les langages de programmation.

 En c#, le `VarArgs` convention d’appel est utilisée lors de la liste des paramètres d’une méthode se termine par le `__arglist` mot clé. Visual Basic ne prend pas en charge la `VarArgs` convention d’appel et Visual C++ permet son utilisation uniquement dans le code non managé qui utilise l’ellipse `...` notation.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle en c#, utilisez le [params](/dotnet/csharp/language-reference/keywords/params) mot clé au lieu de `__arglist`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre deux méthodes, un qui enfreint la règle et qui satisfait à la règle.

 [!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.CallingConventions?displayProperty=fullName>
- [Indépendance du langage et composants indépendants du langage](/dotnet/standard/language-independence-and-language-independent-components)