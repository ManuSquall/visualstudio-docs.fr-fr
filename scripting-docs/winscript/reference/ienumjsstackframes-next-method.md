---
title: "Ienumjsstackframes::Next, méthode | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumJsStackFrames.Next
apilocation: jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2068bd130e7eb03747b89e2ba107019aa1cd458
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ienumjsstackframesnext-method"></a>IEnumJsStackFrames::Next, méthode
Obtient le nombre spécifié de frames.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [out] Le nombre de frames retourné.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IEnumJsStackFrames](../../winscript/reference/ienumjsstackframes-interface.md)