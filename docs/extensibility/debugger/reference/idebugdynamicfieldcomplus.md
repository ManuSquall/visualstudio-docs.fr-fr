---
title: "IDebugDynamicFieldCOMPlus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugDynamicFieldCOMPlus"
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugDynamicFieldCOMPlus
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

représente un champ dynamique pour un objet d' [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .  
  
## Syntaxe  
  
```  
IDebugDynamicFieldCOMPlus : IDebugDynamicField  
```  
  
## Méthodes  
 En plus de les méthodes sur l'interface d' [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) , cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|Récupère un type donné son type primitif.|  
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|Récupère un type donné son jeton.|  
  
## Configuration requise  
 en\-tête : Sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll