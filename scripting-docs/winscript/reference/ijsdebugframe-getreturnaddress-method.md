---
title: "Ijsdebugframe::getreturnaddress, méthode | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugFrame.GetReturnAddress
apilocation: jscript9diag.dll
ms.assetid: 7f10c1d6-d7b9-402e-9020-04cded37f9d3
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9d2b78f049a080f70b30edb82af1066817f6adb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframegetreturnaddress-method"></a>IJsDebugFrame::GetReturnAddress, méthode
Obtient l’adresse de retour envoyée à la 'start' (voir GetStackRange) de l’image.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetReturnAddress(  
   UINT64 *pReturnAddress  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pReturnAddress`  
 [out] L’adresse de retour.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)