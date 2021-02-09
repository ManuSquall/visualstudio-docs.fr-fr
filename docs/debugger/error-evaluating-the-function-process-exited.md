---
title: Le processus cible s’est terminé avec le code de code &apos; &apos; lors de l’évaluation de la fonction de fonction &apos; &apos; | Microsoft Docs
ms.date: 4/06/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 07891e5bcbcab35a4ec5652676a014b87dd32d43
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871635"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>Erreur : le processus cible s’est terminé avec le code &#39;code&#39; lors de l’évaluation de la fonction &#39;fonction&#39;

Texte complet du message : le processus cible s’est terminé avec le code’code’lors de l’évaluation de la fonction’Function'.

Pour faciliter l’inspection de l’état des objets .NET, le débogueur force automatiquement le processus débogué à exécuter du code supplémentaire (en général, les méthodes et les fonctions de l’accesseur Get de la propriété `ToString` ). Dans la plupart des scénarios, ces fonctions s’exécutent correctement ou lèvent des exceptions qui peuvent être interceptées par le débogueur. Toutefois, dans certaines circonstances, les exceptions ne peuvent pas être interceptées, car elles traversent les limites du noyau, nécessitent la pompage des messages utilisateur ou ne sont pas récupérables. Par conséquent, une méthode Getter ou ToString de propriété qui exécute du code qui termine explicitement le processus (par exemple, appelle `ExitProcess()` ) ou lève une exception non gérée qui ne peut pas être interceptée (par exemple, `StackOverflowException` ) met fin au processus débogué et met fin à la session de débogage. Si vous rencontrez ce message d’erreur, cela s’est produit.

Ce problème est souvent dû au fait que lorsque le débogueur évalue une propriété qui s’appelle elle-même, cela peut entraîner une exception de dépassement de capacité de la pile. L’exception de dépassement de capacité de la pile ne peut pas être récupérée et le processus cible se termine.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

Il existe deux solutions possibles à ce problème.

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Solution #1 : empêcher le débogueur d’appeler la propriété Getter ou la méthode ToString 

Le message d’erreur indique le nom de la fonction que le débogueur a essayé d’appeler. Avec le nom de la fonction, vous pouvez essayer de réévaluer cette fonction à partir de la fenêtre **exécution** pour déboguer l’évaluation. Le débogage est possible lors de l’évaluation à partir de la fenêtre **exécution** car, contrairement aux évaluations implicites des fenêtres **automatique/variables locales/espion** , le débogueur s’arrête sur les exceptions non gérées.

Si vous pouvez modifier cette fonction, vous pouvez empêcher le débogueur d’appeler la méthode ou l’accesseur Get de propriété `ToString` . Essayez l’une des opérations suivantes :

* Remplacez la méthode par un autre type de code, en plus d’une méthode Getter ou d’une méthode ToString de propriété. le problème disparaît.
    -ou-
* (Pour `ToString` ) Définissez un `DebuggerDisplay` attribut sur le type et vous pouvez faire en sorte que le débogueur évalue autre chose que `ToString` .
    -ou-
* (Pour un accesseur Get de propriété) Placez l' `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` attribut sur la propriété. Cela peut être utile si vous avez une méthode qui doit rester une propriété pour des raisons de compatibilité d’API, mais qu’elle doit être une méthode.

Si vous ne pouvez pas modifier cette méthode, vous pourrez peut-être interrompre le processus cible à une autre instruction et retenter l’évaluation.

### <a name="solution-2-disable-all-implicit-evaluation"></a>#2 de solution : désactiver toutes les évaluations implicites

Si les solutions précédentes ne résolvent pas le problème, accédez à **Outils**  >  **options** et décochez la case définir le **débogage**  >  **général**  >  **activer l’évaluation de la propriété et d’autres appels de fonction implicite**. Cela désactivera la plupart des évaluations de fonctions implicites et devrait résoudre le problème.
