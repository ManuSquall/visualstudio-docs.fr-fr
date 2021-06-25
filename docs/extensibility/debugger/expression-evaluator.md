---
title: Évaluateur d’expression | Microsoft Docs
description: En savoir plus sur les évaluateurs d’expression, qui examinent la syntaxe d’un langage pour analyser et évaluer des variables et des expressions au moment de l’exécution en mode arrêt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 998f361d8008257cb8f4a888b4d4fbb985c9c977
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900978"
---
# <a name="expression-evaluator"></a>Évaluateur d’expression
Les évaluateurs d’expression (EE) examinent la syntaxe d’un langage pour analyser et évaluer des variables et des expressions au moment de l’exécution, ce qui leur permet d’être affichées par l’utilisateur lorsque l’IDE est en mode arrêt.

## <a name="use-expression-evaluators"></a>Utiliser les évaluateurs d’expression
 Les expressions sont créées à l’aide de la méthode [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) , comme suit :

1. Le moteur DE débogage (DE) implémente l’interface [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .

2. Le package de débogage obtient un `IDebugExpressionContext2` objet à partir d’une interface [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , puis appelle la `IDebugStackFrame2::ParseText` méthode sur celui-ci pour obtenir un objet [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .

3. Le package de débogage appelle la méthode [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou la méthode [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour récupérer la valeur de l’expression. `IDebugExpression2::EvaluateAsync` est appelé à partir de la fenêtre commande/exécution. Tous les autres composants de l’interface utilisateur appellent `IDebugExpression2::EvaluateSync` .

4. Le résultat de l’évaluation de l’expression est un objet [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , qui contient le nom, le type et la valeur du résultat de l’évaluation de l’expression.

   Au cours de l’évaluation de l’expression, EE requiert des informations du composant fournisseur de symboles. Le fournisseur de symboles fournit les informations symboliques utilisées pour identifier et comprendre l’expression analysée.

   Lorsque l’évaluation DE l’expression asynchrone est terminée, un événement asynchrone est envoyé par le à l’aide du gestionnaire DE débogage de session (SDM) pour notifier l’IDE que l’évaluation de l’expression est terminée. Et, le résultat de l’évaluation est ensuite retourné à partir de l’appel à la `IDebugExpression2::EvaluateSync` méthode.

## <a name="implementation-notes"></a>Remarques relatives à l’implémentation
 Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] moteurs de débogage s’attendent à communiquer avec l’évaluateur d’expression à l’aide d’interfaces CLR (Common Language Runtime). Par conséquent, un évaluateur d’expression qui fonctionne avec les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] moteurs de débogage doit prendre en charge le CLR (une liste complète de toutes les interfaces de débogage CLR se trouve dans debugref.doc, qui fait partie du [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] ).

## <a name="see-also"></a>Voir aussi
- [Composants du débogueur](../../extensibility/debugger/debugger-components.md)
