---
title: IDebugApplicationThreadEvents110::OnSuspendForBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110::OnSuspendForBreakPoint
ms.assetid: 224245ac-2aa2-43ae-97ed-493afc3d0122
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3ce1510ad9e7b4560a7aaafb8d65d5b0e6143cf
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349632"
---
# <a name="idebugapplicationthreadevents110onsuspendforbreakpoint"></a>IDebugApplicationThreadEvents110::OnSuspendForBreakPoint
Détermine si le thread a entièrement suspendu pour un point d’arrêt et n’a pas encore repris l’exécution normale.  
  
> [!IMPORTANT]
>  [IDebugApplicationThreadEvents110 (Interface)](../../winscript/reference/idebugapplicationthreadevents110-interface.md) est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnSuspendForBreakPoint( void );  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’a aucun paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplicationThreadEvents110 Interface](../../winscript/reference/idebugapplicationthreadevents110-interface.md)