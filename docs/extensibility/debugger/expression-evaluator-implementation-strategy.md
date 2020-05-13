---
title: Stratégie de mise en œuvre de l’évaluateur de l’expression (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3922689c20c839b3c0c2b2440bc9fefd5d25c80a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738669"
---
# <a name="expression-evaluator-implementation-strategy"></a>Stratégie de mise en œuvre de l’évaluateur d’expression
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, consultez [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Une approche pour créer rapidement un évaluateur d’expression (EE) consiste d’abord à implémenter le code minimum nécessaire pour afficher les variables locales dans la fenêtre **local.** Il est utile de se rendre compte que chaque ligne dans la fenêtre **Locals** affiche le nom, le type et la valeur d’une variable locale, et que tous les trois sont représentés par un objet [IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md) Le nom, le type et la valeur d’une variable locale sont obtenus à partir d’un `IDebugProperty2` objet en appelant sa méthode [GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Pour plus d’informations sur la façon d’afficher les variables locales dans la fenêtre **local,** voir [Afficher les habitants](../../extensibility/debugger/displaying-locals.md).

## <a name="discussion"></a>Discussions
 Une séquence de mise en œuvre possible commence par la mise en œuvre [de IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Les méthodes [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) et [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) doivent être mises en œuvre pour afficher les habitants. `IDebugExpressionEvaluator::GetMethodProperty` L’appel `IDebugProperty2` renvoie un objet qui représente une méthode : c’est-à-dire un objet [IDebugMethodField.](../../extensibility/debugger/reference/idebugmethodfield.md) Les méthodes elles-mêmes ne sont pas affichées dans la fenêtre **des sections locales.**

 La méthode [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) devrait être mise en œuvre ensuite. Le moteur de débogé (DE) appelle cette méthode pour `IDebugProperty2::EnumChildren` obtenir `guidFilter` une `guidFilterLocalsPlusArgs`liste de variables locales et d’arguments en passant un argument de . `IDebugProperty2::EnumChildren`appelle [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) et [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinant les résultats dans un recensement unique. Voir [les habitants de Display](../../extensibility/debugger/displaying-locals.md) pour plus de détails.

## <a name="see-also"></a>Voir aussi
- [Mettre en œuvre un évaluateur d’expression](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Afficher les habitants](../../extensibility/debugger/displaying-locals.md)
