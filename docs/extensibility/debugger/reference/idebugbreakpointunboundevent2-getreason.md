---
title: "IDebugBreakpointUnboundEvent2::GetReason | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointUnboundEvent2::GetReason"
helpviewer_keywords: 
  - "IDebugBreakpointUnboundEvent2::GetReason"
ms.assetid: 0f8a4fec-d3eb-417d-8516-4f7b51904033
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBreakpointUnboundEvent2::GetReason
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient la raison que le point d'arrêt a été annulé la liaison.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetReason(   
   BP_UNBOUND_REASON* pdwUnboundReason  
);  
```  
  
```c#  
int GetReason(   
   out enum_ BP_UNBOUND_REASON pdwUnboundReason  
);  
```  
  
#### Paramètres  
 `pdwUnboundReason`  
 \[out\]  Retourne une valeur de l'énumération de [BP\_UNBOUND\_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md) spécifiant la raison que le point d'arrêt a été annulé la liaison.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Les raisons incluent un point d'arrêt est relié à nouveau à un emplacement différent après l'opération de modification\-et\-continuation, ou une détermination qu'un point d'arrêt a été lié dans l'erreur.  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet **de CBreakpointUnboundDebugEventBase** qui expose l'interface d' [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) .  
  
```cpp#  
STDMETHODIMP CBreakpointUnboundDebugEventBase::GetReason(  
    BP_UNBOUND_REASON* pdwUnboundReason)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( EVAL(pdwUnboundReason) )  
    {  
        *pdwUnboundReason = m_dwReason;  
  
        hRes = S_OK;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```  
  
## Voir aussi  
 [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)