---
title: "Contexte d’&#233;valuation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "évaluation de l’expression [Debugging SDK], le débogage"
  - "évaluation d’expression, contexte"
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Contexte d’&#233;valuation
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Lorsque le moteur de débogage \(DE\) appelle l’évaluateur d’expression \(EE\), trois arguments passés à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) déterminer le contexte pour rechercher et évaluer des symboles, comme indiqué dans le tableau suivant.  
  
## Arguments  
  
|Argument|Description|  
|--------------|-----------------|  
|`pSymbolProvider`|Un [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) interface qui spécifie le Gestionnaire de symboles \(es\) à utiliser pour identifier le symbole.|  
|`pAddress`|Un [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interface qui spécifie le point d’exécution actuel. Cela permet de trouver la méthode qui contient le code en cours d’exécution.|  
|`pBinder`|Un [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interface qui peut être utilisé pour rechercher la valeur et le type d’un symbole de fonction de son nom.|  
  
 `IDebugParsedExpression::EvaluateSync` Retourne un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface qui représente la valeur résultante et son type.  
  
## Voir aussi  
 [Interfaces d’évaluateur d’Expression clé](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Afficher les variables locales](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)