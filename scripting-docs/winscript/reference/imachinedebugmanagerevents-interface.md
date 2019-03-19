---
title: Interface IMachineDebugManagerEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: fcfcc2aed0fedefdc149b83e911d33cd3b54cdef
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153121"
---
# <a name="imachinedebugmanagerevents-interface"></a>IMachineDebugManagerEvents, interface
Signale les modifications apportées à la liste des applications en cours d’exécution tenue à jour par le gestionnaire de débogage d’ordinateur. Cette interface peut être utilisée par l’IDE de débogueur pour afficher une liste dynamique des applications.  
  
 Outre les méthodes héritées de `IUnknown`, le `IMachineDebugManagerEvents` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Gère l’événement lorsqu’une application est ajoutée à l’exécution liste d’applications.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Gère l’événement lorsqu’une application est supprimée de l’exécution liste d’applications.|