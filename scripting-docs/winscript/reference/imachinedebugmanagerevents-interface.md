---
title: IMachineDebugManagerEvents (Interface) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerEvents interface
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 369dc8d182efe7bf9697454d0e4b1c9c1a10c027
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727629"
---
# <a name="imachinedebugmanagerevents-interface"></a>IMachineDebugManagerEvents, interface
Signale les modifications en cours d’exécution liste des applications gérée par le Gestionnaire de débogage d’ordinateur. Cette interface peut être utilisée par le débogueur IDE pour afficher une liste dynamique des applications.  
  
 Outre les méthodes héritées de `IUnknown`, le `IMachineDebugManagerEvents` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Gère l’événement lorsqu’une application est ajoutée à l’exécution liste des applications.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Gère l’événement lorsqu’une application est supprimée de l’exécution liste des applications.|