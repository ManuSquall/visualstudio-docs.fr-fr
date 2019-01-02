---
title: 'Erreur : Évaluation de la fonction &#39;fonction&#39; a expiré et dû être abandonnée de manière unsafe | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 459ece9551ce8bd64703db139f8024ece4953cfa
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648546"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Erreur : Évaluation de la fonction &#39;fonction&#39; a expiré et dû être abandonnée de manière non sécurisée

Texte du message complet : L’évaluation de la fonction 'fonction' a dépassé le délai d’attente et a dû être abandonnée d’une façon non sécurisée Cela a peut-être endommagé le processus cible. 

Pour le rendre plus facile à inspecter l’état d’objets .NET, le débogueur force automatiquement le processus débogué à exécuter du code supplémentaire (en général, les méthodes d’accesseur Get de propriété et les fonctions de ToString). Dans la plupart des scénarios de tous les, ces fonctions s’exécuter rapidement et facilitant le débogage. Toutefois, le débogueur ne s’exécute l’application dans un bac à sable. Par conséquent, un accesseur Get de propriété ou de la méthode ToString qui appelle une fonction native qui se bloque peut entraîner des délais d’expiration longue qui n’est peut-être pas récupérable. Si vous rencontrez ce message d’erreur, cela s’est produite.
 
Une des raisons courantes pour résoudre ce problème sont que lorsque le débogueur évalue une propriété, il autorise uniquement le thread en cours d’inspection pour s’exécuter. Par conséquent, si la propriété est en attente sur d’autres threads de s’exécuter au sein de l’application déboguée, et si elle est en attente d’une manière qui le Runtime .NET n’est pas en mesure d’interruption, ce problème se produit.
 
## <a name="to-correct-this-error"></a>Pour corriger cette erreur
 
Il existe plusieurs solutions possibles à ce problème.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Solution 1 Empêcher le débogueur de l’appel de la propriété d’accesseur Get ou la méthode ToString
 
Le message d’erreur vous indiquera le nom de la fonction que le débogueur a essayé d’appeler. Si vous pouvez modifier cette fonction, vous pouvez empêcher le débogueur de l’appel de l’accesseur Get de propriété ou de la méthode ToString. Essayez l’une des opérations suivantes :
 
* Modifier la méthode à un autre type de code en plus d’un accesseur Get de propriété ou méthode ToString et le problème disparaîtra.
    ou
* (Pour ToString) Définir un attribut DebuggerDisplay sur le type et que le débogueur peut évaluer autre chose que ToString.
    ou
* (Pour un accesseur Get de propriété) Placez le `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` attribut sur la propriété. Cela peut être utile si vous avez une méthode qui doit rester une propriété pour des raisons de compatibilité d’API, mais il doit être une méthode.
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Solution 2 Demander le code cible du débogueur pour abandonner l’évaluation
 
Le message d’erreur vous indiquera le nom de la fonction que le débogueur a essayé d’appeler. Si l’accesseur Get de propriété ou de la méthode ToString parfois ne parvient pas à s’exécuter correctement, en particulier dans les situations où le problème est que le code doit exécuter du code d’un autre thread, la fonction de l’implémentation peut appeler `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` pour demander au débogueur d’abandon de la fonction version d’évaluation. Avec cette solution, il est toujours possible d’évaluer explicitement ces fonctions, mais le comportement par défaut est que l’exécution s’arrête lorsque l’appel de NotifyOfCrossThreadDependency se produit.
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>Solution 3 Désactiver l’évaluation implicite tous les
 
Si les solutions précédentes ne résolvent pas le problème, accédez à **outils** > **Options**et désactivez le paramètre **débogage**  >   **Général** > **activer l’évaluation de la propriété et d’autres appels de fonction implicite**. Cela désactive la plupart des évaluations de fonction implicite et devrait résoudre le problème.

### <a name="solution-4-enable-managed-compatibility-mode"></a>Solution : Activer le mode de compatibilité managé

Si vous basculez vers le moteur de débogage hérité, vous pourrez peut-être éliminer cette erreur. Accédez à **outils** > **Options**, puis sélectionnez le paramètre **débogage** > **général**  >  **Utiliser le mode de compatibilité managé**. Pour plus d’informations, consultez [général d’options de débogage](../debugger/general-debugging-options-dialog-box.md).



  
