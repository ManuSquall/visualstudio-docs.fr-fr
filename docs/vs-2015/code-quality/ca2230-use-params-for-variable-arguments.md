---
title: 'CA2230 : utilisez les paramètres pour les arguments de variable | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ce66e04272618b9df2ab1957af305bb9bf40ee9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540359"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230 : Utilisez le mot clé params pour les arguments de variables
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Category|Microsoft. usage|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause :
 Un type public ou protégé contient une méthode publique ou protégée qui utilise la `VarArgs` Convention d’appel.

## <a name="rule-description"></a>Description de la règle
 La `VarArgs` Convention d’appel est utilisée avec certaines définitions de méthode qui acceptent un nombre variable de paramètres. Une méthode utilisant la `VarArgs` Convention d’appel n’est pas Common Language Specification conforme CLS et peut ne pas être accessible dans les langages de programmation.

 En C#, la `VarArgs` Convention d’appel est utilisée lorsque la liste de paramètres d’une méthode se termine par le `__arglist` mot clé. Visual Basic ne prend pas en charge la `VarArgs` Convention d’appel et Visual C++ autorise uniquement son utilisation dans du code non managé qui utilise la notation d’ellipse `...` .

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle en C#, utilisez le mot clé [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) à la place de `__arglist` .

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant illustre deux méthodes, une qui enfreint la règle et une autre qui satisfait la règle.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>[Indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
