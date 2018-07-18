---
title: Stratégie d’implémentation évaluateur expression | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e67b2496c2e30428cd4cc830526e53cf0cc61fdd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102432"
---
# <a name="expression-evaluator-implementation-strategy"></a>Stratégie d’implémentation expression évaluateur
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Créer rapidement un évaluateur d’expression (EE) consiste à tout d’abord implémenter le code minimal nécessaire pour afficher les variables locales de la **variables locales** fenêtre. Il est utile de savoir que chaque ligne dans le **variables locales** affiche le nom, le type et la valeur d’une variable locale, et que les trois sont représentées par une [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet. Le nom, le type et la valeur d’une variable locale peuvent être obtenus à partir d’un `IDebugProperty2` objet en appelant son [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (méthode). Pour plus d’informations sur l’affichage des variables locales de la **variables locales** fenêtre, consultez [afficher les variables locales](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Discussion  
 Une séquence d’implémentation possibles démarre dans l’implémentation de [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Le [analyser](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) et [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) méthodes doivent être implémentées pour afficher les variables locales. Appel de `IDebugExpressionEvaluator::GetMethodProperty` retourne un `IDebugProperty2` objet qui représente une méthode : autrement dit, un [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) objet. Les méthodes elles-mêmes ne sont pas affichés dans le **variables locales** fenêtre.  
  
 Le [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) méthode doit être implémentée en regard. Le moteur de débogage (DE) appelle cette méthode pour obtenir une liste d’arguments et variables locales en passant `IDebugProperty2::EnumChildren` un `guidFilter` argument de `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren` appels [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) et [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinant les résultats dans une énumération unique. Consultez [afficher les variables locales](../../extensibility/debugger/displaying-locals.md) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’un évaluateur d’Expression](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Affichage des variables locales](../../extensibility/debugger/displaying-locals.md)