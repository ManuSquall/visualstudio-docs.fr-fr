---
title: Interfaces d’évaluateur d’Expression de clé | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe0c592c65e2c6ab7429cef44a830325a834ecdc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103846"
---
# <a name="key-expression-evaluator-interfaces"></a>Interfaces d’évaluateur d’Expression clé
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Lorsque vous écrivez un évaluateur d’expression (EE), ainsi que le contexte d’évaluation, vous devez être familiarisé avec les interfaces suivantes.  
  
## <a name="interface-descriptions"></a>Descriptions de l’interface  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     A une méthode unique, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), qui obtient une structure de données qui représente le point en cours d’exécution. Cette structure de données est un des trois arguments qui passe par le moteur de débogage (Allemagne) à la [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) méthode pour évaluer une expression. Cette interface est généralement implémentée par le fournisseur de symboles.  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     A la [lier](../../extensibility/debugger/reference/idebugbinder-bind.md) méthode qui obtient la zone de mémoire qui contient la valeur actuelle d’un symbole. Étant donné à la fois la méthode conteneur, représentée par une [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objet et au symbole lui-même, représenté par une [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objet, `IDebugBinder::Bind` retourne la valeur du symbole. `IDebugBinder` est généralement implémentée par le DE.  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     Représente un type de données simple. Pour des types complexes, tels que les tableaux et les méthodes, utilisez dérivé [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) et [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) des interfaces, respectivement. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) est une autre interface dérivée importante qui représente les symboles contenant d’autres symboles, tels que les méthodes ou les classes. Le `IDebugField` interface (et ses dérivés) sont généralement implémentées par le fournisseur de symboles.  
  
     Un `IDebugField` objet peut être utilisé pour rechercher le nom et le type d’un symbole et, avec un [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) d’objet, peut être utilisé pour rechercher sa valeur.  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     Représente les bits réelles de la valeur de l’exécution d’un symbole. [Lier](../../extensibility/debugger/reference/idebugbinder-bind.md) prend un [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objet, qui représente un symbole et retourne un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objet. Le [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) méthode retourne la valeur du symbole dans une mémoire tampon. En général, un D’implémente cette interface pour représenter la valeur d’une propriété dans la mémoire.  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     Cette interface représente l’évaluateur d’expression lui-même. La méthode clé est [analyser](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), qui retourne un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interface.  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     Cette interface représente une expression analysée prête à être évaluée. La méthode clé est [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) qui retourne un IDebugProperty2 représentant la valeur et le type de l’expression.  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     Cette interface représente une valeur et son type et est le résultat d’une évaluation d’expression.  
  
## <a name="see-also"></a>Voir aussi  
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md)