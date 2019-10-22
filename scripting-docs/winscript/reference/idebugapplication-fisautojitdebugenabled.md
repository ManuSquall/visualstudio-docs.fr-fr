---
title: 'IDebugApplication :: FIsAutoJitDebugEnabled | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FIsAutoJitDebugEnabled
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FIsAutoJitDebugEnabled
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9bf97a4d3985dd3dd32e582c689fde0ecd6f52e1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574991"
---
# <a name="idebugapplicationfisautojitdebugenabled"></a>IDebugApplication::FIsAutoJitDebugEnabled
Détermine si un débogueur juste-à-temps (JIT) est inscrit pour les hôtes passifs de débogage automatique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’accepte aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 Si la méthode est réussie et qu’un débogueur JIT est inscrit pour les hôtes passifs de débogage automatique, la méthode retourne `TRUE`. Sinon, il retourne `FALSE`.  
  
## <a name="remarks"></a>Notes  
 Cette méthode détermine si un débogueur JIT est inscrit pour les hôtes passifs de débogage automatique.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)