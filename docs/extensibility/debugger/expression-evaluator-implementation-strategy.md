---
title: Stratégie d’implémentation de l’évaluateur d’expression | Microsoft Docs
description: En savoir plus sur une stratégie de création d’un évaluateur d’expression en implémentant d’abord du code pour afficher les variables locales dans la fenêtre variables locales.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d7527c361a889d5aa1f19ec7a211f8aeb8dcbd15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921386"
---
# <a name="expression-evaluator-implementation-strategy"></a>Stratégie d’implémentation de l’évaluateur d’expression
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Une approche permettant de créer rapidement un évaluateur d’expression (EE) consiste d’abord à implémenter le code minimal nécessaire pour afficher les variables locales dans la fenêtre variables **locales** . Il est utile de se rendre compte que chaque ligne de la fenêtre **variables locales** affiche le nom, le type et la valeur d’une variable locale, et que les trois sont représentés par un objet [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) . Le nom, le type et la valeur d’une variable locale sont obtenus à partir d’un `IDebugProperty2` objet en appelant sa méthode [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . Pour plus d’informations sur l’affichage des variables locales dans la fenêtre variables **locales** , consultez Affichage des variables [locales](../../extensibility/debugger/displaying-locals.md).

## <a name="discussion"></a>Discussions
 Une séquence d’implémentation possible commence par l’implémentation de [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Les méthodes [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) et [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) doivent être implémentées pour afficher les variables locales. L’appel de `IDebugExpressionEvaluator::GetMethodProperty` retourne un `IDebugProperty2` objet qui représente une méthode : autrement dit, un objet [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) . Les méthodes elles-mêmes ne sont pas affichées dans la fenêtre **variables locales** .

 La méthode [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) doit être implémentée par la suite. Le moteur de débogage (DE) appelle cette méthode pour obtenir la liste des variables et des arguments locaux en passant `IDebugProperty2::EnumChildren` un `guidFilter` argument de `guidFilterLocalsPlusArgs` . `IDebugProperty2::EnumChildren` appelle [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) et [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), en combinant les résultats dans une énumération unique. Pour plus d’informations, consultez [afficher les variables locales](../../extensibility/debugger/displaying-locals.md) .

## <a name="see-also"></a>Voir aussi
- [Implémenter un évaluateur d’expression](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Afficher les variables locales](../../extensibility/debugger/displaying-locals.md)
