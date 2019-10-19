---
title: 'IApplicationDebugger :: onHandleBreakPoint | Microsoft Docs'
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
ms.openlocfilehash: 3796ea1f50f0c4bcf945dbc10592c048db22757b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577839"
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
 dans Thread où le point d’arrêt s’est produit.  
  
 `br`  
 dans Raison du point d’arrêt.  
  
 `pError`  
 dans Informations d’erreur d’exécution, fournies lorsque la valeur de `br` est BREAKREASON_ERROR.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée lorsqu’un point d’arrêt est atteint et `IDebugApplication::HandleBreakPoint` est appelée.  
  
 L’application restera suspendue jusqu’à ce que l’IDE du débogueur appelle `IRemoteDebugApplication::ResumeFromBreakPoint`.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)  
 [IDebugApplication :: HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)    
 [IRemoteDebugApplication :: ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)    
 [Énumération BREAKREASON](../../winscript/reference/breakreason-enumeration.md)