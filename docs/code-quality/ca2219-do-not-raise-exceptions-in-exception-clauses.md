---
title: "CA2219 : Ne pas lever d’exceptions dans les clauses d’exception | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8c5a4ee1d4425b3967928171648453a631aea815
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219 : Ne pas lever d'exceptions dans les clauses d'exception
|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInExceptionClauses|  
|CheckId|CA2219|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Sans rupture, rupture|  
  
## <a name="cause"></a>Cause  
 Une exception est levée depuis une `finally`, filtre ou une clause fault.  
  
## <a name="rule-description"></a>Description de la règle  
 Lorsqu’une exception est levée dans une clause d’exception, il augmente considérablement la difficulté du débogage.  
  
 Lorsqu’une exception est levée dans un `finally` ou une clause fault, la nouvelle exception masque l’exception active, le cas échéant. Cela rend l’erreur d’origine difficile à détecter et à déboguer.  
  
 Lorsqu’une exception est levée dans une clause de filtre, l’exécution en mode silencieux intercepte l’exception et provoque le filtre doit évaluer sur false. Il n’existe aucun moyen de faire la différence entre l’évaluation de filtre à false et qu’une exception soit levée à partir d’un filtre. Cela rend difficile à détecter et déboguer des erreurs dans la logique du filtre.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour résoudre cette violation de cette règle, ne levez pas explicitement d’exception à partir d’un `finally`, filtre ou une clause fault.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. Il n’existe aucun scénario dans lequel une exception levée dans une clause d’exception présente un avantage au code en cours d’exécution.  
  
## <a name="related-rules"></a>Règles associées  
 [CA1065 : Ne levez pas d’exceptions dans des emplacements inattendus](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Avertissements liés à la conception](../code-quality/design-warnings.md)