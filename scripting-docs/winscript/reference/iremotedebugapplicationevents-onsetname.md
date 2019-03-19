---
title: IRemoteDebugApplicationEvents::OnSetName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnSetName
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnSetName
ms.assetid: 524dcff3-fb48-4d8f-8989-73eb539454fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cf72bb02a1ef934fcbf6a4fa32c9572a6e1afa7
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153056"
---
# <a name="iremotedebugapplicationeventsonsetname"></a>IRemoteDebugApplicationEvents::OnSetName
Gère un événement de nom de jeu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnSetName(  
   LPCOLESTR  pstrName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrName`  
 [in] Le nouveau nom.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode gère un événement de nom de jeu.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)