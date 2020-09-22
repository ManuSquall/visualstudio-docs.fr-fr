---
title: L’évaluation de la fonction de fonction &apos; &apos; a expiré et devait être abandonnée de manière non sécurisée | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 256b7858ed5714d716b31fa28c8cd463b96dbb8a
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852743"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Erreur : l’évaluation de la fonction &#39;fonction&#39; a dépassé le délai d’attente et devait être abandonnée de manière non sécurisée

Texte complet du message : l’évaluation de la fonction’fonction’a expiré et devait être abandonnée de manière non sécurisée. Cela peut avoir endommagé le processus cible.

Pour faciliter l’inspection de l’état des objets .NET, le débogueur force automatiquement le processus débogué à exécuter du code supplémentaire (en général, les méthodes d’accesseur Get de propriété et les fonctions ToString). Dans la plupart des scénarios, ces fonctions se terminent rapidement et facilitent grandement le débogage. Toutefois, le débogueur n’exécute pas l’application dans un bac à sable (sandbox). Par conséquent, une méthode Getter ou ToString de propriété qui appelle une fonction native qui ne répond plus peut entraîner des délais d’attente longs qui peuvent ne pas être récupérables. Si vous rencontrez ce message d’erreur, cela s’est produit.

Ce problème est souvent dû au fait que lorsque le débogueur évalue une propriété, il autorise uniquement le thread en cours d’inspection à s’exécuter. Par conséquent, si la propriété attend que d’autres threads s’exécutent à l’intérieur de l’application déboguée, et si elle attend dans le cas où le Runtime .NET n’est pas en mesure d’interrompre, ce problème se produit.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

Il existe plusieurs solutions possibles à ce problème.

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Solution #1 : empêcher le débogueur d’appeler la propriété Getter ou la méthode ToString

Le message d’erreur indique le nom de la fonction que le débogueur a essayé d’appeler. Si vous pouvez modifier cette fonction, vous pouvez empêcher le débogueur d’appeler la méthode Getter ou ToString de la propriété. Essayez l’une des opérations suivantes :

* Remplacez la méthode par un autre type de code, en plus d’une méthode Getter ou d’une méthode ToString de propriété. le problème disparaît.
    - ou -
* (Pour ToString) Définissez un attribut DebuggerDisplay sur le type et vous pouvez faire en sorte que le débogueur évalue autre chose que ToString.
    - ou -
* (Pour un accesseur Get de propriété) Placez l' `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` attribut sur la propriété. Cela peut être utile si vous avez une méthode qui doit rester une propriété pour des raisons de compatibilité d’API, mais qu’elle doit être une méthode.

### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>#2 de solution : demandez au débogueur d’abandonner l’évaluation du code cible

Le message d’erreur indique le nom de la fonction que le débogueur a essayé d’appeler. Si la méthode Getter ou ToString de la propriété ne parvient pas à s’exécuter correctement, en particulier dans les situations où le problème est que le code a besoin d’un autre thread pour exécuter le code, la fonction d’implémentation peut appeler `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` pour demander au débogueur d’abandonner l’évaluation de la fonction. Avec cette solution, il est toujours possible d’évaluer explicitement ces fonctions, mais le comportement par défaut est que l’exécution s’arrête lorsque l’appel NotifyOfCrossThreadDependency se produit.

### <a name="solution-3-disable-all-implicit-evaluation"></a>#3 de solution : désactiver toutes les évaluations implicites

Si les solutions précédentes ne résolvent pas le problème, accédez à **Outils**  >  **options**et décochez la case définir le **débogage**  >  **général**  >  **activer l’évaluation de la propriété et d’autres appels de fonction implicite**. Cela désactivera la plupart des évaluations de fonctions implicites et devrait résoudre le problème.

### <a name="solution-4-enable-managed-compatibility-mode"></a>#4 de solution : activer le mode de compatibilité managé

Si vous basculez vers le moteur de débogage hérité, vous pourrez peut-être éliminer cette erreur. Accédez à **Outils**  >  **options**, puis sélectionnez le paramètre définir le **débogage**  >  **général**  >  **utiliser le mode de compatibilité managé**. Pour plus d’informations, consultez [options de débogage générales](../debugger/general-debugging-options-dialog-box.md).
