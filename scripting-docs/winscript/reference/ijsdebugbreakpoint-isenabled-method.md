---
title: "Ijsdebugbreakpoint::IsEnabled, méthode | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJSDebugBreakPoint.IsEnabled
apilocation: jscript9diag.dll
ms.assetid: 39b63f49-2a0d-41b7-a2ba-75dcb06251a9
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb7ab887b8e3442a0c38ea403ad43bdea10cdd66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugbreakpointisenabled-method"></a>IJsDebugBreakPoint::IsEnabled, méthode
Détermine si le point d’arrêt est activé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsEnabled(  
   BOOL *pIsEnabled  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pIsEnabled`  
 [out] Retourne la valeur true si le point d’arrêt est activé ; Sinon, retourne false.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Remarques  
 Retourne E_UNEXPECTED si elle est appelée sur un point d’arrêt supprimé.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)