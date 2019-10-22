---
title: 'IDebugApplication :: RemoveStackFrameSniffer | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.RemoveStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::RemoveStackFrameSniffer
ms.assetid: 00304b88-e435-4b87-a331-44e7492eb32d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 605daf51214ba5af9d6010b28be9569453ca7962
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571110"
---
# <a name="idebugapplicationremovestackframesniffer"></a>IDebugApplication::RemoveStackFrameSniffer
Supprime un fournisseur d’énumérateur de frame de pile de cette application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT RemoveStackFrameSniffer(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwCookie`  
 dans Cookie retourné par la méthode `AddStackFrameSniffer` lorsque le fournisseur d’énumérateur de frame de pile a été ajouté.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 La méthode `RemoveStackFrameSniffer` supprime un fournisseur d’énumérateur de frame de pile de cette application.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplication :: AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)    
 @No__t_1 de l' [interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [Interface IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)