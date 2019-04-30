---
title: Stratégie d’implémentation évaluateur expression | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2ded111c371fc1a42c8f1ee08769f5b06aeda
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421163"
---
# <a name="expression-evaluator-implementation-strategy"></a>Stratégie d’implémentation d’un évaluateur d’expression
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Pour créer rapidement un évaluateur d’expression (EE) consiste à implémenter tout d’abord le code minimal nécessaire pour afficher les variables locales dans le **variables locales** fenêtre. Il est utile à l’esprit que chaque ligne dans le **variables locales** fenêtre affiche le nom, le type et la valeur d’une variable locale, et que toutes les trois sont représentées par un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet. Le nom, le type et la valeur d’une variable locale peuvent être obtenus à partir d’un `IDebugProperty2` objet en appelant son [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (méthode). Pour plus d’informations sur l’affichage des variables locales dans le **variables locales** fenêtre, consultez [affichant les variables locales](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Discussion  
 Une séquence d’implémentation possibles commence par implémentation [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Le [analyser](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) et [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) méthodes doivent être implémentées pour afficher les variables locales. Appel `IDebugExpressionEvaluator::GetMethodProperty` retourne un `IDebugProperty2` objet qui représente une méthode : autrement dit, un [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) objet. Méthodes eux-mêmes ne sont pas affichés dans le **variables locales** fenêtre.  
  
 Le [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) méthode doit être implémentée ensuite. Le moteur de débogage (dé) appelle cette méthode pour obtenir une liste des variables locales et des arguments en passant `IDebugProperty2::EnumChildren` un `guidFilter` argument de `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren` appels [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) et [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinant les résultats dans une seule énumération. Consultez [affichant les variables locales](../../extensibility/debugger/displaying-locals.md) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’un évaluateur d’Expression](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Affichage des variables locales](../../extensibility/debugger/displaying-locals.md)
