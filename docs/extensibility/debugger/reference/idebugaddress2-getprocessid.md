---
title: IDebugAddress2::GetProcessID | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12a2b5c056dd34ebba9690306134e20e78b94bcb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842805"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
Récupère l’ID de processus qui possède l’objet représenté par ce [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetProcessID (  
   DWORD* pProcID  
);  
```  
  
```csharp  
int GetProcessID (  
   out uint pProcID  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pProcID`  
 [out] L’ID de processus.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)