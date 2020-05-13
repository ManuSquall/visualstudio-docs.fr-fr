---
title: Contexte d’évaluation (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e3d02bd652d6c46b5aabe00e049e425f0921c27
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738804"
---
# <a name="evaluation-context"></a>Contexte d'évaluation
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, consultez [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Lorsque le moteur de débopathie (DE) appelle l’évaluateur d’expression (EE), trois arguments qui sont passés à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) déterminent le contexte pour trouver et évaluer les symboles, comme indiqué dans le tableau suivant.

## <a name="arguments"></a>Arguments

|Argument|Description|
|--------------|-----------------|
|`pSymbolProvider`|Une interface [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) qui spécifie le gestionnaire de symbole (SH) à utiliser pour identifier le symbole.|
|`pAddress`|Une interface [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) qui spécifie le point d’exécution actuel. Cette interface trouve la méthode qui contient le code exécuté.|
|`pBinder`|Une interface [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) qui trouve la valeur et le type d’un symbole donné son nom.|

 `IDebugParsedExpression::EvaluateSync`retourne une interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) représentant la valeur résultante et son type.

## <a name="see-also"></a>Voir aussi
- [Interfaces d’évaluateur d’expression clés](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Affichage des habitants](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
