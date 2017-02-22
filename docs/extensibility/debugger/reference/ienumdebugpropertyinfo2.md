---
title: "IEnumDebugPropertyInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPropertyInfo2"
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo2"
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugPropertyInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface énumère les structures de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) .  
  
## Syntaxe  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 le moteur de débogage \(DE\) implémente cette interface pour représenter les informations pour une propriété particulière.  
  
## Remarques pour les appelants  
 appelez [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) pour obtenir cette interface représentant les enfants d'une propriété particulière.  appelez [EnumProperties](../Topic/IDebugStackFrame2::EnumProperties.md) pour obtenir cette interface représentant les propriétés d'un frame de pile particulier.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IEnumDebugPropertyInfo2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Suivant](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Récupère un nombre spécifié de structures de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) dans une séquence d'énumération.|  
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Ignore un nombre spécifié de structures de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) dans une séquence d'énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|réinitialise une séquence d'énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
|[GetCount](../Topic/IEnumDebugPropertyInfo2::GetCount.md)|obtient le nombre de structures de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) dans un énumérateur.|  
  
## Notes  
 En général une propriété est une hiérarchie des informations qui peut inclure un nom, les évaluer, y remédier, puis tapez, ainsi que toutes les autres informations pertinentes à l'objet ou au frame de pile associé de propriété.  Pour plus d'informations, consultez [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md).  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../Topic/IDebugStackFrame2::EnumProperties.md)