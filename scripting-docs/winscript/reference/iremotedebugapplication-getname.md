---
title: 'IRemoteDebugApplication :: GetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.GetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::GetName
ms.assetid: 3a8e8a4b-d7d4-40e5-97a1-f6d18db2e9c4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5689eb9153be0e9b6442ba505d618966f1421d39
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572005"
---
# <a name="iremotedebugapplicationgetname"></a>IRemoteDebugApplication::GetName
Retourne le nom de ce nœud d’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetName(  
   BSTR*  pbstrName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrName`  
 à Nom de ce nœud d’application.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le nom de ce nœud d’application.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)