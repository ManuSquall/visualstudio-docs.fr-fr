---
title: IApplicationDebugger::onHandleBreakPoint | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onHandleBreakPoint
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onHandleBreakPoint
ms.assetid: 31adcecd-d6c1-4222-ab2c-32ec2fefb322
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3be067d3b8c3e3268ac2caf1614b70efff6f665
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725299"
---
# <a name="iapplicationdebuggeronhandlebreakpoint"></a>IApplicationDebugger::onHandleBreakPoint
Gère un événement de point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `prpt`  
 [in] Le thread sur lequel le point d’arrêt s’est produite.  
  
 `br`  
 [in] La raison pour le point d’arrêt.  
  
 `pError`  
 [in] Informations d’erreur de runtime, fourni quand la valeur de `br` est BREAKREASON_ERROR.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est appelée lorsqu’un point d’arrêt est atteint et `IDebugApplication::HandleBreakPoint` est appelée.  
  
 L’application reste en pause jusqu'à ce que le débogueur IDE appelle `IRemoteDebugApplication::ResumeFromBreakPoint`.  
  
## <a name="see-also"></a>Voir aussi  
 [IApplicationDebugger (Interface)](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)   
 [IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)   
 [Énumération BREAKREASON](../../winscript/reference/breakreason-enumeration.md)