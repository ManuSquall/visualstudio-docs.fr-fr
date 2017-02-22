---
title: "IDebugPointerObject3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugPointerObject3"
ms.assetid: 11d26af4-1079-435e-96fa-d5269cbea8eb
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPointerObject3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Représente un pointeur dans une arborescence d’analyse et étend la **IDebugPointerObject** interface.  
  
## Syntaxe  
  
```  
IDebugPointerObject3 : IDebugPointerObject  
```  
  
## Notes relatives à l'attention des implémenteurs  
 Un évaluateur d’expression \(EE\) implémente cette interface.  
  
## Méthodes  
 Outre les méthodes sur le [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) interface, cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetPointerAddress](../../../extensibility/debugger/reference/idebugpointerobject3-getpointeraddress.md)|Récupère l’adresse du pointeur.|  
  
## Configuration requise  
 En\-tête : Ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll