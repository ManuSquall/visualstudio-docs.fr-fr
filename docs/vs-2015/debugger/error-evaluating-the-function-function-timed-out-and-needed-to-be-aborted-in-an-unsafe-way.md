---
title: 'Erreur : l’évaluation de la fonction &#39;&#39; a dépassé le délai d’attente et devait être abandonnée de manière non sécurisée | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.assetid: 0a9f70ed-21ad-4a10-8535-b9c5885ad8f4
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a27bf67770eef770fddef0301a804e6c45579539
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387120"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Erreur : l’évaluation de la fonction &#39;fonction&#39; a dépassé le délai d’attente et devait être abandonnée de manière non sécurisée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Texte complet du message : l’évaluation de la fonction’fonction’a expiré et devait être abandonnée de manière non sécurisée. Cela peut avoir endommagé le processus cible. 

Pour faciliter l’inspection de l’état des objets .NET, le débogueur force automatiquement le processus débogué à exécuter du code supplémentaire (en général, les méthodes d’accesseur Get de propriété et les fonctions ToString). Dans la plupart des scénarios, ces fonctions se terminent rapidement et facilitent grandement le débogage. Toutefois, le débogueur n’exécute pas l’application dans un bac à sable (sandbox). Par conséquent, une méthode Getter ou ToString de propriété qui appelle une fonction native qui ne répond plus peut entraîner des délais d’attente longs qui peuvent ne pas être récupérables. Si vous rencontrez ce message d’erreur, cela s’est produit.
 
Ce problème est souvent dû au fait que lorsque le débogueur évalue une propriété, il autorise uniquement le thread en cours d’inspection à s’exécuter. Par conséquent, si la propriété attend que d’autres threads s’exécutent à l’intérieur de l’application déboguée, et si elle attend dans le cas où le Runtime .NET n’est pas en mesure d’interrompre, ce problème se produit.
 
## <a name="to-correct-this-error"></a>Pour corriger cette erreur
 
Il existe trois solutions possibles à ce problème.
 
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
 
Si les solutions précédentes ne résolvent pas le problème, accédez à *Outils*  /  *options*et décochez la case définir le *débogage*  /  *général*  /  *activer l’évaluation de la propriété et d’autres appels de fonction implicite*. Cela désactivera la plupart des évaluations de fonctions implicites et devrait résoudre le problème.
