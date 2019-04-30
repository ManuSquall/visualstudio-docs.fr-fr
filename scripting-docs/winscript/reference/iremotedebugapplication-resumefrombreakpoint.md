---
title: IRemoteDebugApplication::ResumeFromBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ResumeFromBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ResumeFromBreakPoint
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5844381188cb03c99ab0a44ed9b9e0fdbab67e6e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944171"
---
# <a name="iremotedebugapplicationresumefrombreakpoint"></a>IRemoteDebugApplication::ResumeFromBreakPoint
Continue une application en cours d’un point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `prptFocus`  
 [in] Pour le pas à pas de modes, le thread qui doit être affecté par le mode pas à pas.  
  
 `bra`  
 [in] L’action à entreprendre lors de la reprise de l’application.  
  
 `era`  
 [in] L’action à entreprendre dans le cas où l’application est arrêtée en raison d’une erreur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode continue d’une application en cours d’un point d’arrêt.  
  
## <a name="see-also"></a>Voir aussi  
 [IRemoteDebugApplication (Interface)](../../winscript/reference/iremotedebugapplication-interface.md)   
 [Énumération BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)   
 [Énumération ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)