---
title: "IDebugProperty2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2"
helpviewer_keywords: 
  - "Interface de IDebugProperty2"
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProperty2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface représente une propriété du frame de pile, une propriété de document de programme, ou une autre propriété.  La propriété est généralement le résultat d'une évaluation de l'expression.  
  
> [!NOTE]
>  Cette utilisation de « propriété » ne doit pas être confondue avec cette signification une variable membre d'une classe, bien qu' `IDebugProperty2` puisse représenter une telle entité.  
  
## Syntaxe  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface pour représenter un type particulier de valeur.  Par exemple, la valeur peut être une valeur numérique à la suite d'une évaluation de l'expression, d'un contexte de mémoire utilisé pour restituer la mémoire, ou d'une liste de registres et de leurs valeurs.  
  
## Remarques pour les appelants  
 appelez [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour obtenir cette interface, qui représente le résultat d'une évaluation.  `IDebugExpression2::EvaluateAsync` retourne cette interface en envoyant une interface d' [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) au SDM, qui appelle ensuite [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) pour récupérer la propriété.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) retourne cette interface pour fournir le document associé de script.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) retourne cette interface pour représenter la valeur de retour d'une fonction.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) retourne cette interface pour représenter différentes propriétés du programme telles qu'un nom ou un contexte de mémoire.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) retourne cette interface pour représenter différentes propriétés du frame de pile telles que des variables locales.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugProperty2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Remplit une structure de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) qui décrit une propriété.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|définit la valeur d'une propriété d'une chaîne.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|définit la valeur de la propriété de la valeur d'une référence donnée.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|énumère les enfants d'une propriété.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Retourne le parent d'une propriété.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Retourne la propriété qui décrit la propriété la plus dérivée d'une propriété.|  
|[GetMemoryBytes](../Topic/IDebugProperty2::GetMemoryBytes.md)|Retourne les octets de mémoire qui composent la valeur d'une propriété.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Retourne le contexte de la mémoire pour une valeur de propriété.|  
|[GetSize](../Topic/IDebugProperty2::GetSize.md)|Retourne la taille, en octets, de la valeur de propriété.|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Retourne une référence à cette valeur de propriété.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Retourne les informations détaillées d'une propriété.|  
  
## Notes  
 Une propriété, telle qu'elle est représentée par une interface d' `IDebugProperty2` , peut être considérée comme valeur avec un nom, un type, et une adresse.  En plus de spécifications générales, `IDebugProperty2` peut représenter tout ce qui a une structure hiérarchique, avec des parents et des nœuds enfants.  
  
 Une propriété est généralement transitional, durant uniquement si le frame de pile actuel, par exemple.  En revanche, une référence, telle qu'elle est représentée par une interface d' [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , en tant que la valeur reste dans la mémoire.  
  
 L'IDE peut utiliser l'interface d' `IDebugProperty2` pour permettre aux utilisateurs de parcourir et modifier des propriétés au moment de l'exécution.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)