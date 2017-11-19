---
title: IDebugApplicationNode100::SetFilterForEventSink | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationNode100::SetFilterForEventSink
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6db8ea26787427844a92417bf525dba271063cba
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
Définit le filtre sur un particulier [idebugapplicationnodeevents, Interface](../../winscript/reference/idebugapplicationnodeevents-interface.md) implémentation. Il permet de filtrer les nœuds d’application générées par le compilateur l’enfant afin que le PDM n’envoie plus les événements lorsqu’ils sont créés ou supprimés, les débogueurs de script. Par défaut, tous les nœuds seront envoyées.  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 (Interface)](../../winscript/reference/idebugapplicationnode100-interface.md) est implémentée par PDM v10.0 et supérieur. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetFilterForEventSink(        [in] DWORD dwCookie,        [in] APPLICATION_NODE_EVENT_FILTER filter        );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwCookie`  
 Le cookie du filtre.  
  
 `filter`  
 Filtre.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md)