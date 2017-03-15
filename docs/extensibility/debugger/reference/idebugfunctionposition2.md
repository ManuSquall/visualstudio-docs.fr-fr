---
title: "IDebugFunctionPosition2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionPosition2"
helpviewer_keywords: 
  - "Interface de IDebugFunctionPosition2"
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugFunctionPosition2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente une position abstraite d'une fonction dans un document source.  
  
## Syntaxe  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 le moteur de débogage \(DE\) implémente cette interface pour représenter la position d'une fonction dans un document source.  
  
## Remarques pour les appelants  
 Cette interface est fournie dans le cadre d'une union de [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) plus précisément, une structure de [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) \) qui est ensuite une partie de la structure de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , utilisée en créant un point d'arrêt en attente.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugFunctionPosition2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Obtient le nom de la fonction que cette position est associée.|  
|[GetOffset](../Topic/IDebugFunctionPosition2::GetOffset.md)|Obtient l'offset du début de la fonction.|  
  
## Notes  
 La position représentée par cette interface est basé sur le texte, plus particulièrement, une structure de [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)