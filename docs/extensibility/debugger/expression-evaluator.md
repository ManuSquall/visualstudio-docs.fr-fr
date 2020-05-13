---
title: Évaluateur d’expression (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a477aaceb57e6ccd2eb5125fcf9d8af9be59472b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738691"
---
# <a name="expression-evaluator"></a>Évaluateur d’expression
Les évaluateurs d’expression (EE) examinent la syntaxe d’une langue pour analyser et évaluer les variables et les expressions au moment de l’exécution, ce qui leur permet d’être consultés par l’utilisateur lorsque l’IDE est en mode pause.

## <a name="use-expression-evaluators"></a>Utiliser des évaluateurs d’expression
 Les expressions sont créées à l’aide de la méthode [ParseText,](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) comme suit :

1. Le moteur de débogé (DE) implémente l’interface [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md)

2. Le paquet de débaille `IDebugExpressionContext2` obtient un objet à partir d’une interface [IDebugStackFrame2,](../../extensibility/debugger/reference/idebugstackframe2.md) puis appelle la `IDebugStackFrame2::ParseText` méthode sur elle pour obtenir un objet [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md)

3. Le paquet de débaillement appelle la méthode [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou la méthode [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour obtenir la valeur de l’expression. `IDebugExpression2::EvaluateAsync`est appelé à partir de la fenêtre Command/Immediate. Tous les autres composants `IDebugExpression2::EvaluateSync`de l’interface utilisateur appellent .

4. Le résultat de l’évaluation d’expression est un objet [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) qui contient le nom, le type et la valeur du résultat de l’évaluation d’expression.

   Pendant l’évaluation de l’expression, l’EE exige des informations de la composante du fournisseur de symboles. Le fournisseur de symboles fournit les informations symboliques utilisées pour identifier et comprendre l’expression analysée.

   Lorsque l’évaluation de l’expression asynchrone se termine, un événement asynchrone est envoyé par le DE par l’intermédiaire du gestionnaire de débopathie de session (SDM) pour informer l’IDE que l’évaluation d’expression est complète. Et, le résultat de l’évaluation est `IDebugExpression2::EvaluateSync` ensuite retourné de l’appel à la méthode.

## <a name="implementation-notes"></a>Remarques relatives à l’implémentation
 Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] moteurs de déboguer s’attendent à parler avec l’évaluateur d’expression à l’aide des interfaces Common Language Runtime (CLR). En conséquence, un évaluateur d’expression [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] qui fonctionne avec les moteurs de déboguer doit prendre en charge le CLR (une liste complète de [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]toutes les interfaces de débogage CLR peut être trouvé dans debugref.doc, qui fait partie de la ).

## <a name="see-also"></a>Voir aussi
- [Composants Debugger](../../extensibility/debugger/debugger-components.md)
