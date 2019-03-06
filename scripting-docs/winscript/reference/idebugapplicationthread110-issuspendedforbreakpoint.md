---
title: IDebugApplicationThread110::IsSuspendedForBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 5885f6a01ab09ef2d21277c875ff700712cc00fb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349596"
---
# <a name="idebugapplicationthread110issuspendedforbreakpoint"></a>IDebugApplicationThread110::IsSuspendedForBreakPoint
Détermine si [IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) a été appelé sur ce thread et n’est pas encore terminée.  
  
> [!IMPORTANT]
>  [Interface IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsSuspendedForBreakPoint([out, annotation("_Out_")] BOOL * pfIsSuspended);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pfIsSuspended`  
 [out] `true` si le thread est suspendu pour un point d’arrêt, sinon `false`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)