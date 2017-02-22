---
title: "BP_ERROR_RESOLUTION_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_ERROR_RESOLUTION_INFO"
helpviewer_keywords: 
  - "Structure BP_ERROR_RESOLUTION_INFO"
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# BP_ERROR_RESOLUTION_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

décrit la résolution d'un point d'arrêt d'erreur, y compris l'emplacement, le programme, et le thread.  
  
## Syntaxe  
  
```cpp#  
typedef struct _BP_ERROR_RESOLUTION_INFO {   
   BPERESI_FIELDS         dwFields;  
   BP_RESOLUTION_LOCATION bpResLocation;  
   IDebugProgram2*        pProgram;  
   IDebugThread2*         pThread;  
   BSTR                   bstrMessage;  
   BP_ERROR_TYPE          dwType;  
} BP_ERROR_RESOLUTION_INFO;  
```  
  
```c#  
public struct BP_ERROR_RESOLUTION_INFO {   
   public uint                   dwFields;  
   public BP_RESOLUTION_LOCATION bpResLocation;  
   public IDebugProgram2         pProgram;  
   public IDebugThread2          pThread;  
   public string                 bstrMessage;  
   public uint                   dwType;  
};  
```  
  
## Membres  
 `dwFields`  
 Une combinaison des valeurs de spécifier d'énumération de [BPERESI\_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) que les champs de cette structure sont terminé.  
  
 `bpResLocation`  
 l'union de [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) , qui spécifie l'emplacement de résolution de point d'arrêt.  
  
 `pProgram`  
 l'objet d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente l'application dans laquelle l'erreur de point d'arrêt s'est produite.  
  
 `pThread`  
 L'objet d' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le thread sur lequel l'application qui a généré l'erreur de point d'arrêt s'exécute.  
  
 `bstrMessage`  
 Une chaîne contenant tout avertissement ou un message d'erreur provenant de cette résolution d'erreur.  
  
 `dwType`  
 une valeur de l'énumération de [BP\_ERROR\_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) qui spécifie le type d'erreur de point d'arrêt.  
  
## Notes  
 Cette structure est retournée à partir de la méthode d' [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)   
 [BPRESI\_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_ERROR\_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)