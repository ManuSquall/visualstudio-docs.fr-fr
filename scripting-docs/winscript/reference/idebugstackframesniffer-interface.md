---
title: Interface IDebugStackFrameSniffer | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 41fff384bc9075d94fcfa84d94350fec72ebc64a
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348878"
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