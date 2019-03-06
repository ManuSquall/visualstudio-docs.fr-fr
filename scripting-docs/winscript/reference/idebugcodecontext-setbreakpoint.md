---
title: IDebugCodeContext::SetBreakPoint | Microsoft Docs
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
ms.openlocfilehash: f7f0199c111e620d9b1783ed8da7163d10f2e20b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095782"
---
# <a name="idebugcodecontextsetbreakpoint"></a>IDebugCodeContext::SetBreakPoint
Définit ou efface un point d’arrêt à ce contexte de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetBreakPoint(  
   BREAKPOINT_STATE  bps  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bps`  
 [in] Spécifie l’état de point d’arrêt pour ce contexte de code.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode définit ou efface un point d’arrêt à ce contexte de code.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCodeContext (Interface)](../../winscript/reference/idebugcodecontext-interface.md)   
 [Énumération BREAKPOINT_STATE](../../winscript/reference/breakpoint-state-enumeration.md)