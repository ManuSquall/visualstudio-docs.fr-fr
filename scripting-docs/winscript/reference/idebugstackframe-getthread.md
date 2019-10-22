---
title: 'IDebugStackFrame :: GetThread, | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetThread
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetThread
ms.assetid: ece24728-a6b2-4b01-a6f0-0a82b15be39b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51cb000ef20877f4f3f6536cc9a01ae44c2810c8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576734"
---
# <a name="idebugstackframegetthread"></a>IDebugStackFrame::GetThread
Retourne le thread associé à ce frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetThread(  
   IDebugApplicationThread**  ppat  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppat`  
 à Thread associé à ce frame de pile.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le thread associé à ce frame de pile.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)