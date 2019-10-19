---
title: 'IJsDebugStackWalker :: GetNext, méthode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugStackWalker.GetNext
apilocation:
- jscript9diag.dll
ms.assetid: 0b124768-50d3-4a69-876c-1aa337839a4e
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa667402b46a3404c31dfe26307a5893c68ffcc0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574031"
---
# <a name="ijsdebugstackwalkergetnext-method"></a>IJsDebugStackWalker::GetNext, méthode
Obtient le frame suivant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetNext(  
   IJsDebugFrame **ppFrame  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppFrame`  
 à Objet représentant le frame de pile.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 Retourne E_JsDEBUG_OUTSIDE_OF_VM lorsqu’il n’y a plus de frames de pile à énumérer  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugStackWalker](../../winscript/reference/ijsdebugstackwalker-interface.md)