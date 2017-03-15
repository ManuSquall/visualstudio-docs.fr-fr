---
title: "IDebugArrayObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayObject"
helpviewer_keywords: 
  - "IDebugArrayObject (méthode)"
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugArrayObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface représente un objet tableau.  
  
## Syntaxe  
  
```  
IDebugArrayObject : IDebugObject  
```  
  
## Notes relatives à l'attention des implémenteurs  
 L’évaluateur d’expression implémente cette interface pour représenter un tableau.  
  
## Remarques pour les appelants  
 Le [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface pour obtenir cette interface [QueryInterface](/visual-cpp/atl/queryinterface) Si l’objet représente un tableau.  
  
## Méthodes dans l'ordre Vtable  
 Outre les méthodes sur le `IDebugObject` interface, les méthodes suivantes sont implémentées sur le `IDebugArrayObject` interface.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Obtient le nombre d’éléments dans le tableau.|  
|[GetElement](../Topic/IDebugArrayObject::GetElement.md)|Obtient un élément du tableau.|  
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Obtient tous les éléments du tableau.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Obtient le rang du tableau.|  
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Obtient les dimensions du tableau.|  
  
## Notes  
 Un évaluateur d’expression utilise cette interface pour représenter les tableaux dans une arborescence d’analyse.  
  
## Configuration requise  
 En\-tête : ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)