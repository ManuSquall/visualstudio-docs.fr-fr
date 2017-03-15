---
title: "IDebugBreakpointRequest2::GetLocationType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointRequest2::GetLocationType"
helpviewer_keywords: 
  - "IDebugBreakpointRequest2::GetLocationType"
ms.assetid: b6d14c59-d3aa-48ff-8278-f6b5bba9c2f3
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBreakpointRequest2::GetLocationType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le type d'emplacement du point d'arrêt sur cette requête de point d'arrêt.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetLocationType(   
   BP_LOCATION_TYPE* pBPLocationType  
);  
```  
  
```c#  
int GetLocationType(   
   out enum_BP_LOCATION_TYPE pBPLocationType  
);  
```  
  
#### Paramètres  
 `pBPLocationType`  
 \[out\]  Retourne une valeur de l'énumération de [BP\_LOCATION\_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) qui décrit l'emplacement de cette demande de point d'arrêt.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Retourne `E_FAIL` si le champ d' `bpLocation` dans la structure associée de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) est pas valide.  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet simple d' `CDebugBreakpointRequest` qui expose l'interface de[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) .  
  
```  
HRESULT CDebugBreakpointRequest::GetLocationType(BP_LOCATION_TYPE* pBPLocationType)    
{    
   HRESULT hr;    
  
   if (pBPLocationType)    
   {    
      // Set default BP_LOCATION_TYPE.    
      *pBPLocationType = BPLT_NONE;    
  
      // Check if the BPREQI_BPLOCATION flag is set in BPREQI_FIELDS.    
      if (IsFlagSet(m_bpRequestInfo.dwFields, BPREQI_BPLOCATION))    
      {    
         // Get the new BP_LOCATION_TYPE.    
         *pBPLocationType = m_bpRequestInfo.bpLocation.bpLocationType;    
         hr = S_OK;    
      }    
      else    
      {    
         hr = E_FAIL;    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## Voir aussi  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP\_LOCATION\_TYPE](../../../extensibility/debugger/reference/bp-location-type.md)   
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)