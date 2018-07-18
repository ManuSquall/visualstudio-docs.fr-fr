---
title: IDebugCookie::SetDebugCookie | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugCookie.SetDebugCookie
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugCookie::SetDebugCookie
ms.assetid: 9cba3b05-ff81-4fb0-9382-e9338cb9192d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1155b00750cfe2a91625ba0f531622f381467198
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725819"
---
# <a name="idebugcookiesetdebugcookie"></a>IDebugCookie::SetDebugCookie
Définit le cookie d’application de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetDebugCookie(  
   DWORD  dwDebugAppCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwDebugAppCookie`  
 [in] Un cookie qui identifie l’application de débogage.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode définit le cookie d’application de débogage, ce qui permet de plus d’un débogueur à attacher à un processus.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugCookie](../../winscript/reference/idebugcookie-interface.md)