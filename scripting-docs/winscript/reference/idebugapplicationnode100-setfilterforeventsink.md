---
title: 'IDebugApplicationNode100 :: SetFilterForEventSink | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::SetFilterForEventSink
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f85241bee7b35d40bf193a613a6fefda4265be6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574736"
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
Définit le filtre sur une implémentation d' [interface IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md) particulière. Elle permet aux débogueurs de script de filtrer les nœuds d’application enfants générés par le compilateur afin que le PDM n’envoie plus d’événements quand ceux-ci sont créés ou supprimés. Par défaut, tous les nœuds sont envoyés.  
  
> [!IMPORTANT]
> L' [interface IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) est implémentée par PDM v 10.0 et versions ultérieures. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetFilterForEventSink(        [in] DWORD dwCookie,        [in] APPLICATION_NODE_EVENT_FILTER filter        );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwCookie`  
 Cookie du filtre.  
  
 `filter`  
 Filtre.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md)