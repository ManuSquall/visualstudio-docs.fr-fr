---
title: IDebugCodeContext::SetBreakPoint | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugCodeContext.SetBreakPoint
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugCodeContext::SetBreakPoint
ms.assetid: ecd42eae-66fa-40d3-9e47-08b826784108
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a0111deba23f29aa6b7d31a1aed8d729ff4e7fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725829"
---
# <a name="idebugcodecontextsetbreakpoint"></a>IDebugCodeContext::SetBreakPoint
Active ou désactive un point d’arrêt dans ce contexte de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetBreakPoint(  
   BREAKPOINT_STATE  bps  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bps`  
 [in] Spécifie l’état de point d’arrêt pour ce contexte de code.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode définit ou efface un point d’arrêt dans ce contexte de code.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCodeContext (Interface)](../../winscript/reference/idebugcodecontext-interface.md)   
 [Énumération BREAKPOINT_STATE](../../winscript/reference/breakpoint-state-enumeration.md)