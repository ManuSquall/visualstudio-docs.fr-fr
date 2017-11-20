---
title: IDebugApplication::FIsAutoJitDebugEnabled | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.FIsAutoJitDebugEnabled
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::FIsAutoJitDebugEnabled
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 268a10cc829e2d217bb9a90b355405dd8f3b15b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationfisautojitdebugenabled"></a>IDebugApplication::FIsAutoJitDebugEnabled
Détermine si un débogueur de (JIT) juste-à-temps est inscrit dans auto-debug des hôtes passifs.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, et un débogueur JIT est inscrit sur les hôtes passif auto-debug, la méthode retourne `TRUE`. Sinon, il retourne `FALSE`.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode détermine si un débogueur JIT est inscrit dans auto-debug des hôtes passifs.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)