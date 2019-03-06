---
title: IEnumDebugStackFrames::Next | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Next
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Next
ms.assetid: ade3f5b0-8ff3-48a0-9433-270789e6d53e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1366a33a9b6ea4bcfe9e0bb61cf8c61500853e7c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092025"
---
# <a name="ienumdebugstackframesnext"></a>IEnumDebugStackFrames::Next
Récupère un nombre spécifié de segments dans la séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Next(  
   ULONG                       celt,  
   DebugStackFrameDescriptor*  prgdsfd,  
   ULONG*                      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Le nombre de segments à récupérer.  
  
 `prgdsfd`  
 [out] Retourne un tableau de `DebugStackFrameDescriptor` interfaces qui représente les segments en cours de récupération.  
  
 `pceltFetched`  
 [out] Le nombre réel de segments extraites par l’énumérateur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode récupère un nombre spécifié de segments dans la séquence d’énumération.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugStackFrames (Interface)](../../winscript/reference/ienumdebugstackframes-interface.md)   
 [Structure DebugStackFrameDescriptor](../../winscript/reference/debugstackframedescriptor-structure.md)