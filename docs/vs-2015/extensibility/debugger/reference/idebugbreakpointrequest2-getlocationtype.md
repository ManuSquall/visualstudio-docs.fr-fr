---
title: IDebugBreakpointRequest2::GetLocationType | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBreakpointRequest2::GetLocationType
helpviewer_keywords:
- IDebugBreakpointRequest2::GetLocationType
ms.assetid: b6d14c59-d3aa-48ff-8278-f6b5bba9c2f3
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f769ff699e6884f56af9793cf8d7396289ae1b38
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503463"
---
# <a name="idebugbreakpointrequest2getlocationtype"></a>IDebugBreakpointRequest2::GetLocationType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugBreakpointRequest2::GetLocationType](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype).  
  
Obtient le type d’emplacement de point d’arrêt de cette demande de point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetLocationType(   
   BP_LOCATION_TYPE* pBPLocationType  
);  
```  
  
```csharp  
int GetLocationType(   
   out enum_BP_LOCATION_TYPE pBPLocationType  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pBPLocationType`  
 [out] Retourne une valeur de la [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) énumération qui décrit l’emplacement de cette demande de point d’arrêt.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne `E_FAIL` si le `bpLocation` champ associé [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) structure n’est pas valide.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour une simple `CDebugBreakpointRequest` objet qui expose le[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interface.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)

