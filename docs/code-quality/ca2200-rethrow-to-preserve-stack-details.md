---
title: 'CA2200 : Rethrow pour conserver les détails de la pile | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 18fe55136ca501974b33a04513905ff17fe19748
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200 : Levez à nouveau une exception pour conserver les détails de la pile
|||  
|-|-|  
|TypeName|RethrowToPreserveStackDetails|  
|CheckId|CA2200|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Une exception est à nouveau levée et est spécifiée explicitement dans la `throw` instruction.  
  
## <a name="rule-description"></a>Description de la règle  
 Une fois qu’une exception est levée, partie des informations qu’il transporte est la trace de pile. La trace de pile est une liste de la hiérarchie d’appels de méthode qui commence par la méthode qui lève l’exception et se termine par la méthode qui intercepte l’exception. Si une exception est levée à nouveau en spécifiant l’exception dans le `throw` instruction, la trace de pile est redémarrée à la méthode actuelle et la liste d’appels de méthode entre la méthode d’origine qui a levé l’exception et la méthode actuelle est perdue. Pour conserver les informations de trace de pile d’origine avec l’exception, utilisez la `throw` instruction sans spécifier l’exception.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, lever à nouveau l’exception sans la spécification explicite de l’exception.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une méthode, `CatchAndRethrowExplicitly`, ce qui enfreint la règle et une méthode, `CatchAndRethrowImplicitly`, qui satisfait la règle.  
  
 [!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
 [!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]