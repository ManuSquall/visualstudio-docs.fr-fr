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
ms.openlocfilehash: 21d13611a3c4dd11eb691c746f8746347fb9a83b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661968"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025 : Remplacer les arguments répétitifs par un tableau params
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode publique ou protégée dans un type public a plus de trois paramètres, et ses trois derniers paramètres sont du même type.

## <a name="rule-description"></a>Description de la règle
 Utilisez un tableau de paramètres au lieu d’arguments répétés lorsque le nombre exact d’arguments est inconnu et que les arguments de la variable sont du même type, ou peuvent être passés en tant que même type. Par exemple, la méthode <xref:System.Console.WriteLine%2A> fournit une surcharge à usage général qui utilise un tableau de paramètres pour accepter un nombre quelconque d’arguments <xref:System.Object>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez les arguments répétés par un tableau de paramètres.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est toujours possible de supprimer un avertissement de cette règle. Toutefois, cette conception peut entraîner des problèmes d’utilisation.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole cette règle.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RepeatArgs/cs/FxCop.Design.RepeatArgs.cs#1)]
