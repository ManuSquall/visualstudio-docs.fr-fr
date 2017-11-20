---
title: "Ijsdebugbreakpoint::Disable, méthode | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJSDebugBreakPoint.Disable
apilocation: jscript9diag.dll
ms.assetid: f6f2889c-c001-4ee5-8e3f-4f36235e4fad
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c53ff133fb07d256d00668e499e5996ac650230f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugbreakpointdisable-method"></a>IJsDebugBreakPoint::Disable, méthode
Désactive le point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Disable(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Remarques  
 Retourne E_UNEXPECTED si elle est appelée sur un point d’arrêt supprimé. Retourne S_FALSE si elle est appelée sur un point d’arrêt déjà désactivé.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)