---
title: IDebugApplicationThread (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread interface
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e731ba866504c9a3c3c9ad081a90a12b161355d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthread-interface"></a>IDebugApplicationThread, interface
Permet de moteurs de langue et des hôtes pour assurer la synchronisation de thread et mettre à jour les informations d’état de débogage de threads. Cette interface étend la `IRemoteDebugApplicationThread` interface pour fournir un accès non distant vers le thread.  
  
 Outre les méthodes héritées de `IRemoteDebugApplicationThread`, le `IDebugApplicationThread` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Fournit un mécanisme exécuter du code dans le thread d’application à l’appelant.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Détermine si ce thread est le thread en cours d’exécution.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Détermine si ce thread est le thread de débogueur.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Définit la description de ce thread.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|Définit la description de l’état du thread.|