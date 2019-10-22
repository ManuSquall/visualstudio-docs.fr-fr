---
title: 'IRemoteDebugApplication :: ResumeFromBreakPoint | Microsoft Docs'
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
ms.openlocfilehash: 7fead9c14efbe73bd006a5ff3e1cfb10ad40404b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577461"
---
# <a name="iremotedebugapplicationresumefrombreakpoint"></a>IRemoteDebugApplication::ResumeFromBreakPoint
Poursuit une application qui se trouve actuellement dans un point d’arrêt.  
  
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
 dans Pour les modes d’exécution pas à pas, le thread qui doit être affecté par le mode d’exécution pas à pas.  
  
 `bra`  
 dans Action à effectuer après la reprise de l’application.  
  
 `era`  
 dans Action à exécuter si l’application s’est arrêtée en raison d’une erreur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode continue une application qui se trouve actuellement dans un point d’arrêt.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)  
 @No__t_1 de l' [énumération BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)  
 [Énumération ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)