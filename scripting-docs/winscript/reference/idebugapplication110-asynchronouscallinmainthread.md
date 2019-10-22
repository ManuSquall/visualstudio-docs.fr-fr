---
title: 'IDebugApplication110 :: AsynchronousCallInMainThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::AsynchronousCallInMainThread
ms.assetid: 13b80ff0-4bed-48c1-8031-d4147b51bf6c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04c1a2962662d0046c6b9d323a287d580ee0f3e6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577393"
---
# <a name="idebugapplication110asynchronouscallinmainthread"></a>IDebugApplication110::AsynchronousCallInMainThread
Effectue un appel asynchrone sur le thread principal.  
  
> [!IMPORTANT]
> L' [interface IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) est implémentée par PDM v 11.0 et ultérieur. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pptc`  
 Objet d' [interface IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md) à appeler.  
  
 `dwParam1`  
 Premier paramètre de l’appel.  
  
 `dwParam1`  
 Premier paramètre de l’appel.  
  
 `dwParam2`  
 Deuxième paramètre de l’appel.  
  
 `dwParam3`  
 Troisième paramètre de l’appel.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)