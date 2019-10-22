---
title: 'IRemoteDebugApplicationThread :: GetSystemThreadId | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetSystemThreadId
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetSystemThreadId
ms.assetid: 6a6d5f62-4f60-4e87-9206-3c6f2e026d11
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35c281047bd3333f8fdc3945ed97ad3f402c53a4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575228"
---
# <a name="iremotedebugapplicationthreadgetsystemthreadid"></a>IRemoteDebugApplicationThread::GetSystemThreadId
Retourne un identificateur dépendant du système d’exploitation associé au thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetSystemThreadId(  
   DWORD*  dwThreadId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwThreadId`  
 à Identificateur dépendant du système d’exploitation associé au thread.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 La valeur de `dwThreadId` n’a pas besoin d’être unique sur plusieurs ordinateurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)