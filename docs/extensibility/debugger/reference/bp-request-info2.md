---
title: "BP_REQUEST_INFO2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_REQUEST_INFO2"
helpviewer_keywords: 
  - "Structure de BP_REQUEST_INFO2"
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# BP_REQUEST_INFO2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Contient des informations requises pour implémenter un point d'arrêt, y compris le fournisseur GUID, la contrainte et le point de trace.  
  
## Syntaxe  
  
```cpp#  
typedef struct _BP_REQUEST_INFO2 {  
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
   GUID            guidVendor;  
   BSTR            bstrConstraint;  
   BSTR            bstrTracepoint;  
} BP_REQUEST_INFO2;  
```  
  
```c#  
public struct BP_REQUEST_INFO2 {  
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
   public Guid           guidVendor;  
   public string         bstrConstraint;  
   public string         bstrTracepoint;  
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
  
 `guidVendor`  
 GUID du fournisseur.  peut être une valeur NULL.  
  
 `bstrConstraint`  
 nom de la contrainte de point d'arrêt.  peut être une valeur NULL.  
  
 `bstrTracepoint`  
 nom de point de trace.  peut être une valeur NULL.  
  
## Notes  
 cette structure est retournée par la méthode d' [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)   
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)