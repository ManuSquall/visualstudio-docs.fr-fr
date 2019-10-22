---
title: 'IDebugApplicationThread110 :: GetActiveThreadRequestCount | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: e7f038c1d0958701a14899825a2adb0a11cf604d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574488"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
Retourne le nombre de demandes de thread à partir des mécanismes de basculement de thread de PDM en cours de traitement. Ce nombre est généralement 0 ou 1. Toutefois, le nombre peut être plus élevé si un appel de thread commence à traiter mais déclenche un appel synchrone à partir du thread, ou suspend le thread et autorise le traitement des appels entrants (par exemple, en déclenchant un [IRemoteDebugApplicationEvents ](../../winscript/reference/iremotedebugapplicationevents-interface.md)Événement d’interface, émis sur le thread du débogueur).  
  
> [!IMPORTANT]
> L' [interface IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) est implémentée par PDM v 11.0 et ultérieur. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `puiThreadRequests`  
 à Nombre de demandes de thread.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)