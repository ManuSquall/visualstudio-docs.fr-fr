---
title: IDebugStackFrame::GetCodeContext | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetCodeContext
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetCodeContext
ms.assetid: 3dd378f3-e4b7-413e-8812-0f6c72952544
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dadb440017969f3ea4c824c681c726645a5757b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934716"
---
# <a name="idebugstackframegetcodecontext"></a>IDebugStackFrame::GetCodeContext
Retourne le contexte de code actuel associé au frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetCodeContext(  
   IDebugCodeContext**  ppcc  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppcc`  
 [out] Le contexte de code associé au frame de pile.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le contexte de code actuel associé au frame de pile.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)