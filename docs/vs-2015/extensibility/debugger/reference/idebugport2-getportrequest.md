---
title: IDebugPort2::GetPortRequest | Microsoft Docs
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
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9570f1b7e1e77483d0cff001ce09a4b583416e1f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506503"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugPort2::GetPortRequest](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugport2-getportrequest).  
  
Obtient la description d’un port qui a été utilisé précédemment pour créer le port (si disponible).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  Retourne `E_PORT_NO_REQUEST` si un port n'a pas été créé à l’aide un [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) demande de port.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)

