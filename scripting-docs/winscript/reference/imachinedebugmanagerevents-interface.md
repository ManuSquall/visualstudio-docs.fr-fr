---
title: Interface IMachineDebugManagerEvents | Microsoft Docs
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
ms.openlocfilehash: f9aab3d7abeecd22e830c68f174896df0e7df2da
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344026"
---
# <a name="imachinedebugmanagerevents-interface"></a>IMachineDebugManagerEvents, interface
Signale les modifications apportées à la liste des applications en cours d’exécution tenue à jour par le gestionnaire de débogage d’ordinateur. Cette interface peut être utilisée par l’IDE de débogueur pour afficher une liste dynamique des applications.  
  
 Outre les méthodes héritées de `IUnknown`, le `IMachineDebugManagerEvents` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Gère l’événement lorsqu’une application est ajoutée à l’exécution liste d’applications.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Gère l’événement lorsqu’une application est supprimée de l’exécution liste d’applications.|