---
title: "CA1025 : Remplacer les arguments répétitifs par un tableau params | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9e6142ff6670edd6eb1f4cad009b68005b27a86f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
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