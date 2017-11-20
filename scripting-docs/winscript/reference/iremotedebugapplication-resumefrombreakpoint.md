---
title: IRemoteDebugApplication::ResumeFromBreakPoint | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplication.ResumeFromBreakPoint
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplication::ResumeFromBreakPoint
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5da5fdbaaf74f463161f1a98bbad7d4d147b418d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationresumefrombreakpoint"></a>IRemoteDebugApplication::ResumeFromBreakPoint
Continue une application en cours d’un point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `prptFocus`  
 [in] Pour le pas à pas de modes, le thread qui doit être affecté par le mode d’exécution pas à pas.  
  
 `bra`  
 [in] L’action à entreprendre lors de la reprise de l’application.  
  
 `era`  
 [in] L’action à entreprendre dans le cas où l’application est arrêtée en raison d’une erreur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode continue d’une application en cours d’un point d’arrêt.  
  
## <a name="see-also"></a>Voir aussi  
 [IRemoteDebugApplication (Interface)](../../winscript/reference/iremotedebugapplication-interface.md)   
 [Énumération BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)   
 [Énumération ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)