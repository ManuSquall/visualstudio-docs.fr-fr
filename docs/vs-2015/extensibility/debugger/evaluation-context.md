---
title: Contexte d’évaluation | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7dae6ddcb0c75f0dcbc2207465aed522a4210159
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840158"
---
# <a name="evaluation-context"></a>Contexte d’évaluation
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Lorsque le moteur DE débogage appelle l’évaluateur d’expression (EE), trois arguments passés à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) déterminent le contexte de recherche et d’évaluation des symboles, comme indiqué dans le tableau suivant.  
  
## <a name="arguments"></a>Arguments  
  
|Argument|Description|  
|--------------|-----------------|  
|`pSymbolProvider`|Interface [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) qui spécifie le gestionnaire de symboles (SH) à utiliser pour identifier le symbole.|  
|`pAddress`|Interface [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) qui spécifie le point d’exécution actuel. Cela peut être utilisé pour rechercher la méthode qui contient le code en cours d’exécution.|  
|`pBinder`|Interface [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) qui peut être utilisée pour rechercher la valeur et le type d’un symbole en fonction de son nom.|  
  
 `IDebugParsedExpression::EvaluateSync` retourne une interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) représentant la valeur résultante et son type.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces d’évaluateur d’expression clés](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Affichage des variables locales](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
