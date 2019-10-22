---
title: 'IDebugApplication110 :: SynchronousCallInMainThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::SynchronousCallInMainThread
ms.assetid: 57475ae5-1520-45ef-800d-ccfc6235a5d1
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db2b94d51cc5c9a65355aae7405fb162f564e0cc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573648"
---
# <a name="idebugapplication110synchronouscallinmainthread"></a>IDebugApplication110::SynchronousCallInMainThread
Effectue un appel synchrone sur le thread principal.  
  
> [!IMPORTANT]
> L' [interface IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) est implémentée par PDM v 11.0 et ultérieur. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
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