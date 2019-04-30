---
title: IDebugApplicationThread110::AsynchronousCallIntoThread | Microsoft Docs
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
ms.openlocfilehash: fd9fe0b7177c95aec675faaaa85896c52b375084
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440559"
---
# <a name="idebugapplicationthread110asynchronouscallintothread"></a>IDebugApplicationThread110::AsynchronousCallIntoThread
Effectue un appel asynchrone sur le thread principal.  
  
> [!IMPORTANT]
> [Interface IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pptc`  
 Le [IDebugThreadCall (Interface)](../../winscript/reference/idebugthreadcall-interface.md) objet à appeler.  
  
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