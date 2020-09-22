---
title: Implémentation d’un évaluateur d’expression | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e82e6f1fb4e6f78c7fb1f614144f9a836d9676fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839434"
---
# <a name="implementing-an-expression-evaluator"></a>Implémentation d’un évaluateur d’expression
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L’évaluation d’une expression est une interaction complexe entre le moteur DE débogage (DE), le fournisseur de symboles (SP), l’objet Binder et l’évaluateur d’expression (EE) lui-même. Ces quatre composants sont connectés par des interfaces implémentées par un composant et consommées par un autre composant.  
  
 L’EE prend une expression de l’une sous la forme d’une chaîne et l’analyse ou l’évalue. L’EE implémente les interfaces suivantes, qui sont consommées par l’un des éléments suivants :  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
  L’EE appelle l’objet Binder fourni par le de, pour récupérer la valeur des symboles et des objets. L’EE utilise les interfaces suivantes, qui sont implémentées par l’un des éléments suivants :  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
  L’EE implémente [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` fournit le mécanisme pour décrire le résultat d’une évaluation d’expression, telle qu’une variable locale, une primitive ou un objet, à Visual Studio, qui affiche ensuite les informations appropriées dans la fenêtre **variables locales**, **Espion**ou **exécution** .  
  
  Le SP est donné au EE par le DE lorsqu’il demande des informations. Le SP implémente des interfaces qui décrivent les adresses et les champs, tels que les interfaces suivantes et leurs dérivées :  
  
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
  L’EE utilise toutes ces interfaces.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Stratégie d’implémentation d’un évaluateur d’expression](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Définit un processus en trois étapes pour la stratégie d’implémentation de l’évaluateur d’expression (EE).  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture d’un évaluateur d’expression de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
