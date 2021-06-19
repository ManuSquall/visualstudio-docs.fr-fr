---
title: Savoir qui transmet une valeur de paramètre incorrecte | Microsoft Docs
description: Vous pouvez déterminer quel code appelle votre fonction et en passant une valeur de paramètre incorrecte. Apprenez à utiliser un point d’arrêt conditionnel pour effectuer cette opération.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b2f747e2f92b7817530fe12e14f8f95a9bfbe791
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386915"
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
- [FAQ sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)
- [Points d'arrêt](/previous-versions/ktf38f66(v=vs.100))
- [Débogage du code natif](../debugger/debugging-native-code.md)
