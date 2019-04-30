---
title: IEnumDebugStackFrames::Skip | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Skip
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Skip
ms.assetid: d893d6e9-e119-4f14-99d0-bf23dbd2d625
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1548784de8ad2cfc9d6368691da1b68a1bc1e3f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963310"
---
# <a name="ienumdebugstackframesskip"></a>IEnumDebugStackFrames::Skip
Ignore un nombre spécifié de segments dans une séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Nombre de segments dans la séquence d’énumération à ignorer.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode ignore un nombre spécifié de segments dans une séquence d’énumération.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IEnumDebugStackFrames](../../winscript/reference/ienumdebugstackframes-interface.md)