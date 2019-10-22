---
title: 'IDebugApplication :: FCanJitDebug | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FCanJitDebug
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FCanJitDebug
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d68240ffd86935e9936642c09d5131f70b46e9ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576879"
---
# <a name="idebugapplicationfcanjitdebug"></a>IDebugApplication::FCanJitDebug
Détermine si un débogueur juste-à-temps (JIT) est inscrit.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
BOOL FCanJitDebug();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’accepte aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 Si la méthode est réussie et qu’un débogueur JIT est inscrit, la méthode retourne `TRUE`. Sinon, il retourne `FALSE`.  
  
## <a name="remarks"></a>Notes  
 Cette méthode détermine si un débogueur JIT est inscrit.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)