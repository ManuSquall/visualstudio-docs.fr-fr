---
title: IDebugBreakpointResolution2::GetBreakpointType | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointResolution2::GetBreakpointType
helpviewer_keywords:
- IDebugBreakpointResolution2::GetBreakpointType
ms.assetid: 2b707fb9-f703-4c78-91bf-7434f57790a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d3c25a1c83f91de1e97dd4f328ea68c572867f0c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31106628"
---
# <a name="idebugbreakpointresolution2getbreakpointtype"></a>IDebugBreakpointResolution2::GetBreakpointType
Obtient le type du point d’arrêt représenté par cette résolution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetBreakpointType(   
   BP_TYPE* pBPType  
);  
```  
  
```csharp  
int GetBreakpointType(   
   out enum_ BP_TYPE pBPType  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pBPType`  
 [out] Retourne une valeur de la [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) énumération qui spécifie le type de ce point d’arrêt.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne E_FAIL si le `bpResLocation` champ associé [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) structure n’est pas valide.  
  
## <a name="remarks"></a>Notes  
 Le point d’arrêt peut être un code ou un point d’arrêt, par exemple.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour une simple `CDebugBreakpointResolution` objet qui expose la [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) interface.  
  
```  
HRESULT CDebugBreakpointResolution::GetBreakpointType(BP_TYPE* pBPType)    
{    
   HRESULT hr;    
  
   if (pBPType)    
   {    
      // Set default BP_TYPE.    
      *pBPType = BPT_NONE;    
  
      // Check if the BPRESI_BPRESLOCATION flag is set in BPRESI_FIELDS.    
      if (IsFlagSet(m_bpResolutionInfo.dwFields, BPRESI_BPRESLOCATION))    
      {    
         // Set the new BP_TYPE.    
         *pBPType = m_bpResolutionInfo.bpResLocation.bpType;    
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
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)