---
title: IDebugStackFrameSnifferEx::EnumStackFramesEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrameSnifferEx::EnumStackFramesEx
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8969c279e4eb2c2966e297317a25a60f12be68a9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63005717"
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
Retourne un énumérateur de frames de pile pour le thread actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwSpMin`  
 [in] La limite inférieure d’adresse pour l’énumération des frames de pile.  
  
 `ppedsf`  
 [out] Énumérateur de frames de pile pour le thread actuel.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 L’énumérateur de frame de pile retourne les frames à partir du haut de la pile, la trame envoyées le plus récemment. L’énumérateur contient uniquement les frames de pile avec des adresses supérieurs ou égales à `dwSpMin`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugStackFrameSnifferEx](../../winscript/reference/idebugstackframesnifferex-interface.md)