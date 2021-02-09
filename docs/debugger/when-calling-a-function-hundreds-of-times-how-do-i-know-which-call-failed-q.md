---
title: Rechercher l’échec de l’appel lors de l’appel d’une fonction plusieurs fois
description: Consultez une technique permettant de définir un point d’arrêt sur une fonction de telle sorte que l’arrêt se produit uniquement sur l’appel pour lequel la fonction échoue.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.functions
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8937b58277450198d7c0927d93118c492faedfbc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883881"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Lorsque j'appelle une fonction des centaines de fois, comment puis-je savoir quel appel a échoué ?
## <a name="problem-description"></a>Description du problème
 Mon programme échoue lors de l'appel à une certaine fonction, `CnvtV`. Mais cet échec survient probablement après plusieurs centaines d'appels à la fonction par le programme. Si je définis un point d'arrêt d'emplacement sur `CnvtV`, le programme s'arrête à chaque appel de cette fonction, ce que je veux éviter. J'ignore quelles conditions ont provoqué l'échec de l'appel et je ne peux donc pas définir un point d'arrêt conditionnel. Que puis-je faire ?

## <a name="solution"></a>Solution
 Vous pouvez définir un point d’arrêt sur la fonction en affectant au champ **Nombre d’accès** une valeur très élevée que vous ne risquez pas d’atteindre. Dans le cas présent, vous estimez que la fonction `CnvtV` est appelée plusieurs centaines de fois ; vous affectez par conséquent à **Nombre d’accès** la valeur 1 000 ou une valeur supérieure. Exécutez ensuite le programme et patientez jusqu'à l'échec de l'appel. Lorsqu'il échoue, ouvrez la fenêtre Points d'arrêt et examinez la liste des points d'arrêt. Le point d'arrêt que vous avez défini sur `CnvtV` apparaît, suivi du nombre d'accès et du nombre d'itérations restantes :

```cpp
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)
```

 Vous savez à présent que la fonction a échoué au 101e appel. Si vous réinitialisez le point d'arrêt avec un nombre d'accès égal à 101, puis que vous réexécutez le programme, ce dernier s'arrête au niveau de l'appel à `CnvtV` qui a provoqué son échec.

## <a name="see-also"></a>Voir aussi
- [FAQ sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)
- [Définition de points d’arrêt](/previous-versions/ktf38f66(v=vs.100))
- [Débogage du code natif](../debugger/debugging-native-code.md)