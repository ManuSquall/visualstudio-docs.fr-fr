---
title: Contexte d’évaluation | Microsoft Docs
description: 'Lorsque le moteur de débogage appelle l’évaluateur d’expression, les arguments déterminent le contexte de recherche et d’évaluation des symboles : pSymbolProvider, pAddress et pBinder.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6c3ab6fe53ad288089dc88587e06547573d80cb9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898576"
---
# <a name="evaluation-context"></a>Contexte d'évaluation
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Lorsque le moteur DE débogage appelle l’évaluateur d’expression (EE), trois arguments passés à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) déterminent le contexte de recherche et d’évaluation des symboles, comme indiqué dans le tableau suivant.

## <a name="arguments"></a>Arguments

|Argument|Description|
|--------------|-----------------|
|`pSymbolProvider`|Interface [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) qui spécifie le gestionnaire de symboles (SH) à utiliser pour identifier le symbole.|
|`pAddress`|Interface [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) qui spécifie le point d’exécution actuel. Cette interface recherche la méthode qui contient le code en cours d’exécution.|
|`pBinder`|Interface [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) qui recherche la valeur et le type d’un symbole en fonction de son nom.|

 `IDebugParsedExpression::EvaluateSync` retourne une interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) représentant la valeur résultante et son type.

## <a name="see-also"></a>Voir aussi
- [Interfaces d’évaluateur d’expression clés](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Affichage des variables locales](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
