---
title: IDebugBreakpointUnboundEvent2::GetBreakpoint | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakpointUnboundEvent2::GetBreakpoint
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2::GetBreakpoint
ms.assetid: ad73a207-b778-4dc5-b645-5ec668a63333
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 11640da3bcf5ad25aced8bee6fd6d981d658a772
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953561"
---
# <a name="idebugbreakpointunboundevent2getbreakpoint"></a>IDebugBreakpointUnboundEvent2::GetBreakpoint
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient le point d’arrêt s’est détaché.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetBreakpoint(   
   IDebugBoundBreakpoint2** ppBP  
);  
```  
  
```csharp  
int GetBreakpoint(   
   out IDebugBoundBreakpoint2 ppBP  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppBP`  
 [out] Retourne un [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) objet qui représente le point d’arrêt s’est détaché.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un **CBreakpointUnboundDebugEventBase** objet qui expose le [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) interface.  
  
```cpp#  
STDMETHODIMP CBreakpointUnboundDebugEventBase::GetBreakpoint(  
    IDebugBoundBreakpoint2 **ppbp)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppbp )  
    {  
        if ( m_pbp )  
        {  
            IDebugBoundBreakpoint2 *pibp;  
  
            hRes = m_pbp->QueryInterface(IID_IDebugBoundBreakpoint2, (void **) & pibp);  
  
            if ( S_OK == hRes )  
                *ppbp = pibp;  
        }  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)   
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
