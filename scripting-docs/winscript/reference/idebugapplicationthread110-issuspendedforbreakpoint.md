---
title: 'IDebugApplicationThread110 :: IsSuspendedForBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::IsSuspendedForBreakPoint
ms.assetid: 60688222-557f-4a43-a19b-846cee393cd0
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0e70993b95ccffcf6041bb04f37af90667fc4fd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574455"
---
# <a name="idebugapplicationthread110issuspendedforbreakpoint"></a>IDebugApplicationThread110::IsSuspendedForBreakPoint
Détermine si [IDebugApplicationThreadEvents110 :: OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) a été appelé sur ce thread et s’il n’est pas encore terminé.  
  
> [!IMPORTANT]
> L' [interface IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) est implémentée par PDM v 11.0 et ultérieur. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsSuspendedForBreakPoint([out, annotation("_Out_")] BOOL * pfIsSuspended);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pfIsSuspended`  
 [out] `true` si le thread est suspendu pour un point d’arrêt, sinon `false`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)