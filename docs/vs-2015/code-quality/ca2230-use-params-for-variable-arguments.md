---
title: 'CA2230 : Utilisez params pour les arguments de variables | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b591ca9ba3ad56fec5dde1a8df11d7cc4abcecf4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193620"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230 : Utilisez le mot clé params pour les arguments de variables
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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
 Pour corriger une violation de cette règle en c#, utilisez le [params](http://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) mot clé au lieu de `__arglist`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre deux méthodes, un qui enfreint la règle et qui satisfait à la règle.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.Reflection.CallingConventions?displayProperty=fullName> [Indépendance du langage et composants indépendants du langage](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



