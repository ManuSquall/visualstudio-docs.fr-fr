---
title: "IDebugBreakpointRequest3::GetRequestInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointRequest3::GetRequestInfo2"
helpviewer_keywords: 
  - "IDebugBreakpointRequest3::GetRequestInfo2"
ms.assetid: 33942e4a-0a0a-49e8-a693-004954f6d38a
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugBreakpointRequest3::GetRequestInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode extrait les informations de requête de point d'arrêt qui décrivent cette requête de point d'arrêt.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetRequestInfo2(  
   BPREQI_FIELDS      dwFields,  
   BP_REQUEST_INFO2*  bBPRequestInfo  
);  
```  
  
```c#  
int GetRequestInfo2(  
   enum_BPREQI_FIELDS  dwFields,   
   BP_REQUEST_INFO2[]  bBPRequestInfo  
);  
```  
  
#### Paramètres  
 `dwFields`  
 \[in\]  Une combinaison des indicateurs d'énumération de [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) qui déterminent quels champs d' `pBPRequestInfo` doivent être effectués.  
  
 `bBPRequestInfo`  
 \[out\]  La structure de [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) à accomplir.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, le code d'erreur de retour.  
  
## Notes  
 La quantité d'informations dans cette demande qui est retourné par la méthode d' [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) .  
  
## Voir aussi  
 [IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)