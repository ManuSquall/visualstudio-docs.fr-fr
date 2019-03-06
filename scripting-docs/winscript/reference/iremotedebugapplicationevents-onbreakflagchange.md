---
title: IRemoteDebugApplicationEvents::OnBreakFlagChange | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnBreakFlagChange
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnBreakFlagChange
ms.assetid: 25684454-a0d8-47e0-85f5-2217069a9f45
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91facd7a7055ab5ac9e7666c6a0d171e78c73eed
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086734"
---
# <a name="iremotedebugapplicationeventsonbreakflagchange"></a>IRemoteDebugApplicationEvents::OnBreakFlagChange
Gère un événement lorsque les indicateurs de saut changent.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnBreakFlagChange(  
   APPBREAKFLAGS                   abf,  
   IRemoteDebugApplicationThread*  prdatSteppingThread  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `abf`  
 [in] Les indicateurs de saut en cours pour l’application.  
  
 `prdatSteppingThread`  
 [in] Le thread en cours d’exécution.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode gère l’événement lors de la modification de l’indicateur d’arrêt.  
  
## <a name="see-also"></a>Voir aussi  
 [IRemoteDebugApplicationEvents (Interface)](../../winscript/reference/iremotedebugapplicationevents-interface.md)   
 [Énumération APPBREAKFLAGS](../../winscript/reference/appbreakflags-enumeration.md)