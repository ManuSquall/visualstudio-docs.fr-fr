---
title: Savoir qui transmet une valeur de paramètre incorrecte | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.parameters
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42884cd6498f00cfe2df2d0396ff9ea6b03c2f98
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734236"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Comment puis-je savoir d'où provient une valeur de paramètre incorrecte ?
## <a name="problem-description"></a>Description du problème
 Une valeur de paramètre incorrecte est passée à l'une de mes fonctions. Cette fonction est appelée à partir de différents endroits. Comment puis-je savoir d'où provient la valeur incorrecte ?

## <a name="solution"></a>Solution

#### <a name="to-resolve-this-problem"></a>Pour résoudre ce problème

1. Définissez un point d'arrêt d'emplacement au début de la fonction.

2. Cliquez avec le bouton droit sur le point d’arrêt et sélectionnez **Condition**.

3. Dans la boîte de dialogue **Condition de point d’arrêt**, cochez la case **Condition**. Consultez [points d’arrêt avancés](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

4. Entrez une expression, telle que `Var==3`, dans la zone de texte, où `Var` est le nom du paramètre qui contient la valeur incorrecte et où `3` correspond à la valeur incorrecte passée.

5. Activez la case d’option **est true**, puis cliquez sur le bouton **OK**.

6. Réexécutez le programme. Le point d'arrêt provoque l'arrêt du programme au début de la fonction lorsque la valeur du paramètre `Var` est `3`.

7. Utilisez la fenêtre Pile des appels pour rechercher la fonction d'appel et naviguer jusqu'à son code source. Pour plus d’informations, consultez [Comment : utiliser la fenêtre pile des appels](../debugger/how-to-use-the-call-stack-window.md).

## <a name="see-also"></a>Voir aussi
- [Forum Aux Questions sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)
- [Points d’arrêt](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583)
- [Débogage du code natif](../debugger/debugging-native-code.md)