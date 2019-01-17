---
title: IDebugApplication::FIsAutoJitDebugEnabled | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b06d223d76ed741eef6b379ace6b522248ded2e1
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348215"
---
# <a name="idebugapplicationfisautojitdebugenabled"></a>IDebugApplication::FIsAutoJitDebugEnabled
Détermine si un débogueur de (JIT) juste-à-temps est inscrit dans les hôtes stupides automatique-debug.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, et un débogueur JIT est inscrit à des hôtes stupides automatique-debug, la méthode retourne `TRUE`. Sinon, il retourne `FALSE`.  
  
## <a name="remarks"></a>Notes  
 Cette méthode détermine si un débogueur JIT est inscrit auprès des hôtes stupides automatique-debug.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)