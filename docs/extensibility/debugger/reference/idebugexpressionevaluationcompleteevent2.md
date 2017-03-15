---
title: "IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluationCompleteEvent2"
helpviewer_keywords: 
  - "IDebugExpressionEvaluationCompleteEvent2"
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluationCompleteEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface est envoyée par le moteur de \(DE\) débogage au gestionnaire de débogage de session \(SDM\) lorsque l'évaluation de l'expression asynchrone est terminée.  
  
## Syntaxe  
  
```  
IDebugExpressionEvaluationCompleteEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface pour signaler l'achèvement d'une évaluation de l'expression démarrée par un appel à [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  l'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface.  Le SDM utilise [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à l'interface d' `IDebugEvent2` .  
  
## Remarques pour les appelants  
 Le du crée et envoie cet objet événement pour signaler l'achèvement d'une évaluation de l'expression.  L'événement est envoyé à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'elle s'est attachée le programme débogué.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugExpressionEvaluationCompleteEvent2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|obtient l'expression d'origine.|  
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Obtient le résultat de l'évaluation d'une expression.|  
  
## Notes  
 Le De doit envoyer cet événement, que l'évaluation a été réussie ou pas.  
  
 Si l'évaluation n'a pas réussi, les balises d' `DEBUG_PROPINFO_VALUE` et d' `DEBUG_PROPINFO_ATTRIB` ne sont pas définies dans la structure de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) retournée par [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) \(l'objet d' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) est créé par le De et retourné dans l'événement d' `IDebugExpressionEvaluationCompleteEvent2` si l'évaluation a échoué\).  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)