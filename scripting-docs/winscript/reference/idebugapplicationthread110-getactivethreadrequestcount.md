---
title: IDebugApplicationThread110::GetActiveThreadRequestCount | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::GetActiveThreadRequestCount
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8bd776aedd4df61797419795afb8dcc8afeb9318
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348181"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
Retourne le nombre de demandes de thread du thread de PDM commutation des mécanismes qui sont en cours de traitement. Ce nombre est généralement 0 ou 1. Toutefois, le nombre peut être plus élevé si un seul appel de thread commence à traiter mais déclenche un appel synchrone en dehors du thread, ou sinon suspend le thread et autorise les appels entrants à traiter à nouveau (par exemple, en déclenchant un [ IRemoteDebugApplicationEvents Interface](../../winscript/reference/iremotedebugapplicationevents-interface.md) événement, qui est émise sur le thread de débogueur).  
  
> [!IMPORTANT]
>  [Interface IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `puiThreadRequests`  
 [out] Le nombre de demandes de thread.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)