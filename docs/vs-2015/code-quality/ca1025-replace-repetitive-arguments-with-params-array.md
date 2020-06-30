---
title: 'CA1025 : remplacer les arguments répétitifs par un tableau params | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 84809341d7898aeb3defe0447f2a2f1142eb460a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546625"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025 : Remplacer les arguments répétitifs par un tableau params
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode publique ou protégée dans un type public a plus de trois paramètres, et ses trois derniers paramètres sont du même type.

## <a name="rule-description"></a>Description de la règle
 Utilisez un tableau de paramètres au lieu d’arguments répétés lorsque le nombre exact d’arguments est inconnu et que les arguments de la variable sont du même type, ou peuvent être passés en tant que même type. Par exemple, la <xref:System.Console.WriteLine%2A> méthode fournit une surcharge à usage général qui utilise un tableau de paramètres pour accepter un nombre quelconque d' <xref:System.Object> arguments.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez les arguments répétés par un tableau de paramètres.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est toujours possible de supprimer un avertissement de cette règle. Toutefois, cette conception peut entraîner des problèmes d’utilisation.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole cette règle.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RepeatArgs/cs/FxCop.Design.RepeatArgs.cs#1)]
