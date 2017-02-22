---
title: "BP_REQUEST_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_REQUEST_INFO"
helpviewer_keywords: 
  - "Structure BP_REQUEST_INFO"
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# BP_REQUEST_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Contient des informations requises pour implémenter un point d'arrêt.  
  
## Syntaxe  
  
```cpp#  
typedef struct _BP_REQUEST_INFO {  
   BPREQI_FIELDS   dwFields;  
   GUID            guidLanguage;  
   BP_LOCATION     bpLocation;  
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   IDebugThread2*  pThread;  
   BSTR            bstrThreadName;  
   BP_CONDITION    bpCondition;  
   BP_PASSCOUNT    bpPassCount;  
   BP_FLAGS        dwFlags;  
} BP_REQUEST_INFO;  
```  
  
```c#  
public struct BP_REQUEST_INFO {  
   public uint           dwFields;  
   public Guid           guidLanguage;  
   public BP_LOCATION    bpLocation;  
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public IDebugThread2  pThread;  
   public string         bstrThreadName;  
   public BP_CONDITION   bpCondition;  
   public BP_PASSCOUNT   bpPassCount;  
   public uint           dwFlags;  
};  
```  
  
## Membres  
 `dwFields`  
 Une combinaison des indicateurs d'énumération de [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) qui spécifie quels champs sont remplis.  
  
 `guidLanguage`  
 le langage GUID.  
  
 `bpLocation`  
 la structure de [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) qui spécifie le type de l'emplacement du point d'arrêt.  
  
 `pProgram`  
 l'objet d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente l'application dans laquelle le point d'arrêt se produit.  
  
 `bstrProgramName`  
 le nom de l'application dans laquelle le point d'arrêt se produit.  
  
 `pThread`  
 L'objet d' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le thread dans lequel le point d'arrêt se produit.  
  
 `bstrThreadName`  
 Le nom du thread où le point d'arrêt se produit.  
  
 `bpCondition`  
 La structure de [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) qui décrit les conditions dans lesquelles le point d'arrêt le déclenche.  
  
 `bpPassCount`  
 La structure de [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) qui contient des informations sur le nombre à partir de le point d'arrêt.  
  
 `dwFlags`  
 Une combinaison des indicateurs d'énumération de [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) qui spécifie des indicateurs pour le point d'arrêt demandé.  
  
## Notes  
 cette structure est retournée par la méthode d' [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) .  
  
 Si vous devez obtenir le GUID du fournisseur de moteur de débogage, la contrainte de point d'arrêt ou de trace, consultez la structure de [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)