---
title: "IEnumDebugObjects | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugObjects"
helpviewer_keywords: 
  - "Interface de IEnumDebugObjects"
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugObjects
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface représente une collection d’objets implémentant le [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface.  
  
## Syntaxe  
  
```  
IEnumDebugObjects : IUnknown  
```  
  
## Notes relatives à l'attention des implémenteurs  
 L’évaluateur d’expression implémente cette interface pour fournir des ensembles d’objets qui implémentent la [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface. Notez qu’il ne s’agit pas d’une énumération COM standard en raison de la présence de la [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) méthode.  
  
## Remarques pour les appelants  
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) Retourne cette interface.  
  
## Méthodes dans l’ordre Vtable  
 Cette interface implémente les méthodes suivantes.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Suivant](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Récupère l’ensemble suivant de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objets de l’énumération.|  
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Ignore un nombre spécifié d’entrées.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Réinitialise l’énumération à la première entrée.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Récupère une copie de l’énumération actuelle.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Récupère le nombre d’entrées de l’énumération.|  
  
## Notes  
 Cette interface permet à un moteur de débogage énumérer un ensemble d’objets dans un tableau.  
  
## Configuration requise  
 En\-tête : ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)