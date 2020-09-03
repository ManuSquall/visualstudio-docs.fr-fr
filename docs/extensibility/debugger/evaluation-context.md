---
title: Contexte d’évaluation | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738804"
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
