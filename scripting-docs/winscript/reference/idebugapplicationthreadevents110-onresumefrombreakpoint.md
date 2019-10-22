---
title: 'IDebugApplicationThreadEvents110 :: OnResumeFromBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110::OnResumeFromBreakPoint
ms.assetid: 4c97b9a3-fced-487e-a81c-e3f8f2cb7927
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e710d259ae4985f6e37fc14ee70d0467578d2bd0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573352"
---
# <a name="idebugapplicationthreadevents110onresumefrombreakpoint"></a>IDebugApplicationThreadEvents110::OnResumeFromBreakPoint
Le thread reprend à partir d’un point d’arrêt et sera à nouveau actif.  
  
> [!IMPORTANT]
> L' [interface IDebugApplicationThreadEvents110](../../winscript/reference/idebugapplicationthreadevents110-interface.md) est implémentée par PDM v 11.0 et ultérieur. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnResumeFromBreakPoint( void );  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’a aucun paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplicationThreadEvents110 Interface](../../winscript/reference/idebugapplicationthreadevents110-interface.md)