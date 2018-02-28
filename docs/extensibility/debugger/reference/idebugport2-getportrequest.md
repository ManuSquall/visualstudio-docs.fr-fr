---
title: IDebugPort2::GetPortRequest | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 66e0ba17503a0d1bd90358d2cafc3ccec09f6fac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Obtient la description d’un port qui a été précédemment utilisé pour créer le port (si disponible).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPortRequest(   
   IDebugPortRequest2** ppRequest  
);  
```  
  
```csharp  
int GetPortRequest(   
   out IDebugPortRequest2 ppRequest  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppRequest`  
 [out] Retourne un [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) objet qui représente la demande qui a été utilisée pour créer le port.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  Retourne `E_PORT_NO_REQUEST` si un port n'a pas été créé à l’aide un [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) requête sur le port.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Ajouter un port](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)