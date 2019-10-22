---
title: IJsDebugProcess ::P méthode erformAsyncBreak | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.PerformAsyncBreak
apilocation:
- jscript9diag.dll
ms.assetid: 2a6ee369-ea99-4332-8521-a1741ccb6292
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3320c59097dec5229030a3f15252d907562c67e6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577335"
---
# <a name="ijsdebugprocessperformasyncbreak-method"></a>IJsDebugProcess::PerformAsyncBreak, méthode
Met le moteur de script en mode arrêt, provoquant l’arrêt de l’instruction de script suivante.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT PerformAsyncBreak(  
   DWORD threadId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `threadId`  
 dans ID de thread.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)