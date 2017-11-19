---
title: IRemoteDebugApplicationEvents::OnBreakFlagChange | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationEvents.OnBreakFlagChange
apilocation: jscript.dll
helpviewer_keywords: IRemoteDebugApplicationEvents::OnBreakFlagChange
ms.assetid: 25684454-a0d8-47e0-85f5-2217069a9f45
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8b4caac89897f015fec7ac483b967f9b42676aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationeventsonbreakflagchange"></a>IRemoteDebugApplicationEvents::OnBreakFlagChange
Gère un événement lorsque les indicateurs de saut changent.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode gère l’événement lors de la modification de l’indicateur de pause.  
  
## <a name="see-also"></a>Voir aussi  
 [IRemoteDebugApplicationEvents (Interface)](../../winscript/reference/iremotedebugapplicationevents-interface.md)   
 [Énumération APPBREAKFLAGS](../../winscript/reference/appbreakflags-enumeration.md)