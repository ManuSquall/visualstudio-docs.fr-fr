---
title: 'CA1025 : Remplacer les arguments répétitifs par un tableau params'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1ce14b7da80775a9837b5e92f25d141276226cf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025 : Remplacer les arguments répétitifs par un tableau params
|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode publique ou protégée dans un type public a plus de trois paramètres, et ses trois derniers paramètres sont du même type.

## <a name="rule-description"></a>Description de la règle
 Utilisez un tableau de paramètres au lieu d’arguments répétés lorsque le nombre exact d’arguments est inconnu et les arguments variables sont du même type ou peuvent être passés en tant que le même type. Par exemple, le <xref:System.Console.WriteLine%2A> méthode fournit une surcharge à usage général qui utilise un tableau de paramètres pour accepter un nombre quelconque de <xref:System.Object> arguments.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez les arguments répétés avec un tableau de paramètres.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est toujours possible de supprimer un avertissement de cette règle ; Toutefois, cette conception peut entraîner des problèmes d’utilisation.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole cette règle.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]