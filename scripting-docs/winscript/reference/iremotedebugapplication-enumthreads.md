---
title: 'IRemoteDebugApplication :: Enumthreads, | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.EnumThreads
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::EnumThreads
ms.assetid: b4d7294c-1f15-4f7e-bdfd-700e3bf98cea
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 759ecc2da982e840e059e0d96d2b630190527d43
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573847"
---
# <a name="iremotedebugapplicationenumthreads"></a>IRemoteDebugApplication::EnumThreads
Énumère tous les threads connus pour être associés à l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumThreads(  
   IEnumRemoteDebugApplicationThreads**  pperdat  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pperdat`  
 à Énumérateur qui répertorie tous les threads connus pour être associés à l’application.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode énumère tous les threads connus pour être associés à l’application. De nouveaux threads peuvent être ajoutés à tout moment.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)