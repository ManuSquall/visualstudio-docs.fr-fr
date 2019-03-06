---
title: IDebugApplicationNode100::SetFilterForEventSink | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4b273b770a1d82edbf5bbbe26c0865060234b852
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346486"
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
Définit le filtre sur un particulier [IDebugApplicationNodeEvents (Interface)](../../winscript/reference/idebugapplicationnodeevents-interface.md) implémentation. Il permet les débogueurs de script filtrer les nœuds d’application enfants généré par le compilateur afin que le PDM n’envoie plus les événements lorsqu’ils sont créés ou supprimés. Par défaut, tous les nœuds recevront.  
  
> [!IMPORTANT]
>  [Interface IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) est implémentée par PDM v10.0 et supérieure. Trouvée dans activdbg100.h.  
  
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