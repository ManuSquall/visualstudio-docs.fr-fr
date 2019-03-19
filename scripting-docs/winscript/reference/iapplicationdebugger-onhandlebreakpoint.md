---
title: IApplicationDebugger::onHandleBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: edf8816cd646596ce1f897dfd9d949790d52b7b1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148215"
---
# <a name="iapplicationdebuggeronhandlebreakpoint"></a>IApplicationDebugger::onHandleBreakPoint
Gère un événement de point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `prpt`  
 [in] Le thread où le point d’arrêt s’est produite.  
  
 `br`  
 [in] La raison du point d’arrêt.  
  
 `pError`  
 [in] Informations d’erreur de runtime, fourni quand la valeur de `br` est BREAKREASON_ERROR.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée lorsqu’un point d’arrêt est atteint et `IDebugApplication::HandleBreakPoint` est appelée.  
  
 L’application reste en pause jusqu'à ce que l’IDE de débogueur appelle `IRemoteDebugApplication::ResumeFromBreakPoint`.  
  
## <a name="see-also"></a>Voir aussi  
 [IApplicationDebugger (Interface)](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)   
 [IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)   
 [Énumération BREAKREASON](../../winscript/reference/breakreason-enumeration.md)