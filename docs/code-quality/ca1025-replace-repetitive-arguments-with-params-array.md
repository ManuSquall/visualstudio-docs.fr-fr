---
title: 'CA1025 : Remplacer les arguments répétitifs par un tableau params'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5014bfe809cb5d56a22e971833128d1f48d77319
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922968"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025 : Remplacer les arguments répétitifs par un tableau params

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Catégorie|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Une méthode publique ou protégée dans un type public a plus de trois paramètres, et ses trois derniers paramètres sont du même type.

## <a name="rule-description"></a>Description de la règle
Utilisez un tableau de paramètres au lieu d’arguments répétés lorsque le nombre exact d’arguments est inconnu et que les arguments de la variable sont du même type, ou peuvent être passés en tant que même type. Par exemple, la <xref:System.Console.WriteLine%2A> méthode fournit une surcharge à usage général qui utilise un tableau de paramètres pour accepter un nombre <xref:System.Object> quelconque d’arguments.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, remplacez les arguments répétés par un tableau de paramètres.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est toujours possible de supprimer un avertissement de cette règle. Toutefois, cette conception peut entraîner des problèmes d’utilisation.

## <a name="example"></a>Exemple
L’exemple suivant montre un type qui viole cette règle.

[!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]