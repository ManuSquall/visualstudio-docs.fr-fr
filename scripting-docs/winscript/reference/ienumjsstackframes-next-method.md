---
title: Méthode IEnumJsStackFrames::Next | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumJsStackFrames.Next
apilocation:
- jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94e3f478654fadec152aba0690a5474ebbfe02f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963297"
---
# <a name="ienumjsstackframesnext-method"></a>IEnumJsStackFrames::Next, méthode
Obtient le nombre spécifié de frames.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cFrameCount`  
 [in] Le nombre de frames à obtenir.  
  
 `pFrames`  
 [out] Tableau utilisé pour stocker les images.  
  
 `pcFetched`  
 [out] Le nombre de frames retournés.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IEnumJsStackFrames](../../winscript/reference/ienumjsstackframes-interface.md)