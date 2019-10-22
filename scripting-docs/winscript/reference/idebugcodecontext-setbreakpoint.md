---
title: 'IDebugCodeContext :: SetBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: df2bb0395cc1aeaceda3763b2c4016bbd9ba7e1f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573212"
---
# <a name="idebugcodecontextsetbreakpoint"></a>IDebugCodeContext::SetBreakPoint
Définit ou efface un point d’arrêt dans ce contexte de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetBreakPoint(  
   BREAKPOINT_STATE  bps  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bps`  
 dans Spécifie l’état du point d’arrêt pour ce contexte de code.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode définit ou efface un point d’arrêt au niveau de ce contexte de code.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugCodeContext](../../winscript/reference/idebugcodecontext-interface.md)  
 [Énumération BREAKPOINT_STATE](../../winscript/reference/breakpoint-state-enumeration.md)