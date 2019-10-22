---
title: 'IEnumRemoteDebugApplicationThreads :: Clone | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplicationThreads.Clone
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumRemoteDebugApplicationThreads::Clone
ms.assetid: d016e7cf-ae73-48ff-aee7-810222e0b05c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c92e77c748367fce727b64e64008423683bf5798
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573458"
---
# <a name="ienumremotedebugapplicationthreadsclone"></a>IEnumRemoteDebugApplicationThreads::Clone
Crée un énumérateur qui contient le même État que l’énumérateur actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Clone(  
   IEnumRemoteDebugApplicationThreads**  pperdat  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pperdat`  
 à Retourne l’interface `IEnumRemoteDebugApplicationThreads` du clone de l’énumérateur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode crée un énumérateur qui contient le même État que l’énumérateur actuel.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IEnumRemoteDebugApplicationThreads](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)