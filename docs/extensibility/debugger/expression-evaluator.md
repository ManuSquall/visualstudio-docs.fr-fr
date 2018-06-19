---
title: Évaluateur d’expression | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8dd2cc4409dbdb7650454715e133fd76dda5b780
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102315"
---
# <a name="expression-evaluator"></a>Évaluateur d’expression
Évaluateurs d’expression (EE) examiner la syntaxe d’une langue pour analyser et évaluer les variables et les expressions au moment de l’exécution, ce qui permet à être affiché par l’utilisateur lors de l’IDE est en mode arrêt.  
  
## <a name="using-expression-evaluators"></a>À l’aide des évaluateurs d’Expression  
 Les expressions sont créées à l’aide de la [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) méthode, comme suit :  
  
1.  Le moteur de débogage (DE) implémente la [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface.  
  
2.  Le package de débogage Obtient un `IDebugExpressionContext2` à partir de l’objet une [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interface, puis appelle la `IDebugStackFrame2::ParseText` méthode pour obtenir un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objet.  
  
3.  Les appels de package de débogage la [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) méthode ou la [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) méthode pour obtenir la valeur de l’expression. `IDebugExpression2::EvaluateAsync` est appelé à partir de la fenêtre commande/exécution. Tous les autres composants de l’interface utilisateur appellent `IDebugExpression2::EvaluateSync`.  
  
4.  Le résultat de l’évaluation de l’expression est une [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet, qui contient le nom, le type et la valeur du résultat de l’évaluation d’expression.  
  
 Lors de l’évaluation d’expression, le EE requiert des informations à partir du composant de fournisseur de symboles. Le fournisseur de symbole fournit des informations sur les symboles utilisées pour identifier et de comprendre l’expression analysée.  
  
 Lors de l’évaluation de l’expression asynchrone est terminée, un événement asynchrone envoyé par le DE via le Gestionnaire de session de débogage (SDM) pour informer l’IDE que l’évaluation de l’expression est terminée. Lors de l’évaluation d’expression synchrone est terminée, le résultat de l’évaluation est retourné à partir de l’appel à la `IDebugExpression2::EvaluateSync` (méthode).  
  
## <a name="implementation-notes"></a>Remarques d’implémentation  
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] des moteurs de débogage s’attendre à communiquer avec l’évaluateur d’expression à l’aide des interfaces du Common Language Runtime (CLR). Par conséquent, un évaluateur d’expression qui fonctionne avec les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] des moteurs de débogage doivent prendre en charge le CLR (vous trouverez une liste complète de toutes les interfaces de débogage de CLR dans debugref.doc, qui fait partie de la [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]).  
  
## <a name="see-also"></a>Voir aussi  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)