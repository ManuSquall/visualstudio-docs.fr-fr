---
title: IDebugStackFrameSniffer (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 250c104d24f27900a6ff0eb8e8f72644f820bf5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesniffer-interface"></a>IDebugStackFrameSniffer, interface
Fournit un moyen pour énumérer les frames de pile logique connus par un composant. En général, les moteurs de script implémentent cette interface. Le processus débogage Gestionnaire utilise cette interface pour trouver tous les frames de pile associé à un thread donné.  
  
> [!NOTE]
>  Le débogueur appelle cette interface à partir du thread d’intérêt. Le moteur de script doit identifier le thread actuel et retourne un énumérateur approprié.  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes héritées de `IUnknown`, le `IDebugStackFrameSniffer` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Retourne un énumérateur de frames de pile du thread actuel.|