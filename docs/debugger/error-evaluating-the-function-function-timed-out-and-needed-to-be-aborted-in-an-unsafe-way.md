---
title: "Erreur : L’évaluation de la fonction &#39; function &#39; a expiré et nécessaires à l’abandon d’une manière unsafe | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.unsafe_func_eval_abort
ms.assetid: 0a9f70ed-21ad-4a10-8535-b9c5885ad8f4
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 722abd91cb9f97aab67d0d9a5e77ff9e3a4f080d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Erreur : L’évaluation de la fonction &#39; function &#39; a expiré et nécessaires à l’abandon d’une manière non sécurisée

Texte du message complet : évaluation de la fonction 'fonction' a expiré et nécessaires à l’abandon d’une manière non sécurisée. Il a peut-être endommagé le processus cible. 

Pour faciliter l’inspecter l’état des objets .NET, le débogueur force automatiquement le processus débogué à exécuter du code supplémentaire (en général, les méthodes d’accesseur Get de propriété et les fonctions de ToString). Dans la plupart des scénarios de tous les, ces fonctions terminer rapidement et faciliter le débogage. Toutefois, le débogueur ne s’exécute l’application dans un bac à sable. Par conséquent, un accesseur Get de propriété ou de la méthode ToString qui appelle une fonction native qui se bloque peut entraîner des délais d’attente longues qui ne peut pas être récupérée. Si vous rencontrez ce message d’erreur, cela s’est produite.
 
Une des raisons courantes de ce problème sont que lorsque le débogueur évalue une propriété, elle autorise uniquement le thread en cours d’inspection pour exécuter. Par conséquent, si la propriété est en attente sur d’autres threads pour exécuter l’application déboguée, et si elle est en attente d’une façon qui le Runtime .NET n’est pas en mesure d’interruption, ce problème se produit.
 
## <a name="to-correct-this-error"></a>Pour corriger cette erreur
 
Il existe trois solutions possibles à ce problème.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Solution #1 : Empêcher le débogueur à partir de l’appel de la propriété d’accesseur Get ou la méthode ToString
 
Le message d’erreur vous indique le nom de la fonction, que le débogueur a tenté d’appeler. Si vous pouvez modifier cette fonction, vous pouvez empêcher le débogueur de l’appel de l’accesseur Get de propriété ou de la méthode ToString. Essayez l’une des opérations suivantes :
 
* Modifier la méthode en un autre type de code en dehors d’un accesseur Get de propriété ou méthode ToString et le problème disparaîtra.
    ou
* (Pour ToString) Définir un attribut DebuggerDisplay sur le type et que le débogueur peut évaluer autre chose que ToString.
    ou
* (Pour un accesseur Get de propriété) Placez le `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` attribut sur la propriété. Cela peut être utile si vous avez une méthode qui doit rester une propriété pour des raisons de compatibilité d’API, mais il doit être réellement d’une méthode.
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Solution de #2 : Le code cible dans votre demander au débogueur d’abandon de l’évaluation
 
Le message d’erreur vous indique le nom de la fonction, que le débogueur a tenté d’appeler. Si l’accesseur Get de propriété ou méthode ToString parfois ne parvient pas à s’exécuter correctement, en particulier dans les situations où le problème est que le code doit exécuter le code d’un autre thread, puis la fonction de l’implémentation peut appeler `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` pour demander au débogueur d’abandon de la fonction évaluation. Avec cette solution, il est toujours possible d’évaluer explicitement de ces fonctions, mais le comportement par défaut est que l’exécution s’arrête lors de l’appel de NotifyOfCrossThreadDependency se produit.
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>Solution #3 : Désactiver tous les évaluation implicite
 
Si les solutions précédentes ne résout le problème, accédez à *outils* > *Options*et désactivez le paramètre *débogage*  >   *Général* > *activer l’évaluation de la propriété et d’autres appels de fonction implicite*. Cela désactive la plupart des évaluations de fonction implicite et devrait résoudre le problème.



  
