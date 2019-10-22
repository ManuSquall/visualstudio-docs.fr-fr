---
title: IJsDebugBreakPoint ::D méthode désactiver | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.Disable
apilocation:
- jscript9diag.dll
ms.assetid: f6f2889c-c001-4ee5-8e3f-4f36235e4fad
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51e4be2abc8b5a507e091b330de1779cfb14b57e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577734"
---
# <a name="ijsdebugbreakpointdisable-method"></a>IJsDebugBreakPoint::Disable, méthode
Désactive le point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Disable(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 Retourne E_UNEXPECTED s’il est appelé sur un point d’arrêt supprimé. Retourne S_FALSE s’il est appelé sur un point d’arrêt déjà désactivé.  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)