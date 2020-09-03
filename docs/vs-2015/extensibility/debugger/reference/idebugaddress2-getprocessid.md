---
title: 'IDebugAddress2 :: GetProcessID, | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e41e7768432f8b014edef01e80a8e85a4dc200fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165176"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Récupère l’ID du processus qui possède l’objet représenté par cette interface [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) .  
  
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
 à ID du processus.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)
