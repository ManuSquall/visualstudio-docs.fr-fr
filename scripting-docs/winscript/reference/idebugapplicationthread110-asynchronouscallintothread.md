---
title: 'IDebugApplicationThread110 :: AsynchronousCallIntoThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 06b3031a-4aec-4a47-afaa-04642a4c4870
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 595e73787421b5a5e9ca9407dd174c50451051c2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577406"
---
# <a name="idebugapplicationthread110asynchronouscallintothread"></a>IDebugApplicationThread110::AsynchronousCallIntoThread
Effectue un appel asynchrone sur le thread principal.  
  
> [!IMPORTANT]
> L' [interface IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) est implémentée par PDM v 11.0 et ultérieur. Trouvée dans activdbg100.h.  
  
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