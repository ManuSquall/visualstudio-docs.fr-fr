---
title: IRemoteDebugApplicationThread::GetDescription | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetDescription
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetDescription
ms.assetid: 69842e9e-7c1c-4841-a6b2-31505fe85738
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74d3f59648a5a6aa0f510e98b33c3c26b1f9db56
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728479"
---
# <a name="iremotedebugapplicationthreadgetdescription"></a>IRemoteDebugApplicationThread::GetDescription
Obtient la description et l’état de ce thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDescription(  
   BSTR*  pbstrDescription,  
   BSTR*  pbstrState  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrDescription`  
 [out] La description de ce thread.  
  
 `pbstrState`  
 [out] Description de l’état du thread.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode obtient la description et l’état de ce thread.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)