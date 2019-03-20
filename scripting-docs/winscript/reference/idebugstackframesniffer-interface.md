---
title: Interface IDebugStackFrameSniffer | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e753261098133eb97f5010dcef5f602d283aac4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149482"
---
# <a name="idebugstackframesniffer-interface"></a>IDebugStackFrameSniffer, interface
Fournit un moyen pour énumérer les frames de pile logique appelées par un composant. En général, les moteurs de script implémentent cette interface. Le processus débogage Gestionnaire utilise cette interface pour trouver tous les frames de pile associée à un thread donné.  
  
> [!NOTE]
>  Le débogueur appelle cette interface à partir du thread d’intérêt. Le moteur de script doit identifier le thread actuel et retourne un énumérateur approprié.  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes héritées de `IUnknown`, le `IDebugStackFrameSniffer` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Retourne un énumérateur de frames de pile pour le thread actuel.|