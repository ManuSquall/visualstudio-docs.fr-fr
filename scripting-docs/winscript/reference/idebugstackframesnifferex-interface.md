---
title: IDebugStackFrameSnifferEx (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSnifferEx interface
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56d6e63c41db274634b2593989800ea0392b93a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesnifferex-interface"></a>IDebugStackFrameSnifferEx, interface
Fournit un moyen pour énumérer les frames de pile logique connus par un composant. En général, les moteurs de script implémentent cette interface. Le processus débogage Gestionnaire utilise cette interface pour trouver tous les frames de pile associé à un thread donné.  
  
> [!NOTE]
>  Cette interface est appelée à partir du thread d’intérêt. L’implémentation d’interface doit identifier le thread actuel et retourne un énumérateur approprié.  
  
 Outre les méthodes héritées de `IDebugStackFrameSniffer`, le `IDebugStackFrameSnifferEx` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Retourne un énumérateur de frames de pile du thread actuel.|