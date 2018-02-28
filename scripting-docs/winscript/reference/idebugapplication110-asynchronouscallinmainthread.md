---
title: IDebugApplication110::AsynchronousCallInMainThread | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::AsynchronousCallInMainThread
ms.assetid: 13b80ff0-4bed-48c1-8031-d4147b51bf6c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 236a6585d5d5844f282d8ecf5820ac8fdfb49648
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication110asynchronouscallinmainthread"></a>IDebugApplication110::AsynchronousCallInMainThread
Effectue un appel asynchrone sur le thread principal.  
  
> [!IMPORTANT]
>  [IDebugApplication110 (Interface)](../../winscript/reference/idebugapplication110-interface.md) est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pptc`  
 Le [idebugthreadcall, Interface](../../winscript/reference/idebugthreadcall-interface.md) objet à appeler.  
  
 `dwParam1`  
 Le premier paramètre de l’appel.  
  
 `dwParam1`  
 Le premier paramètre de l’appel.  
  
 `dwParam2`  
 Le deuxième paramètre de l’appel.  
  
 `dwParam3`  
 Le troisième paramètre de l’appel.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)