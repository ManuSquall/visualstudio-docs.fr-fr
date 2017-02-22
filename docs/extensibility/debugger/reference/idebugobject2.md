---
title: "IDebugObject2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2"
helpviewer_keywords: 
  - "Interface de IDebugObject2"
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugObject2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface fournit des informations supplémentaires sur un objet.  
  
## Syntaxe  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## Notes relatives à l'attention des implémenteurs  
 L’évaluateur d’expression implémente cette interface pour offrir la prise en charge des alias et des accès aux informations sur l’objet.  
  
## Remarques pour les appelants  
 Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface peut obtenir cette interface à l’aide de [QueryInterface](/visual-cpp/atl/queryinterface). En outre, [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) renvoie cette interface.  
  
## Méthodes dans l’ordre Vtable  
 Outre les méthodes sur le [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface, le `IDebugObject2` interface implémente les éléments suivants :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Obtient le champ ou la variable \(le cas échéant\) qui peut sauvegarder la propriété représentée par cet objet.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Obtient l’objet de code managé qui représente la valeur de cet objet.|  
|[CreateAlias](../Topic/IDebugObject2::CreateAlias.md)|Crée un ID unique pour cet objet, ou retourne un alias existant.|  
|[GetAlias](../Topic/IDebugObject2::GetAlias.md)|Obtient l’alias associé à cet objet, le cas échéant.|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Obtient le type de cet objet.|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Détermine si cet objet représente les données utilisateur.|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Détermine si l’état de modifier & Continuer n’est plus valide.<br /><br /> Un évaluateur d’expression personnalisée n’implémente pas cette méthode \(elle doit toujours retourner `E_NOTIMPL`\).|  
  
## Notes  
 Consultez [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) Pour plus d’informations sur les alias.  
  
## Configuration requise  
 En\-tête : ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de l'évaluation d'expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)