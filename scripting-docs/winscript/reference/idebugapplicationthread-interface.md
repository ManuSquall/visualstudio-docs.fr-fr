---
title: "IDebugApplicationThread, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread (interface)"
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread, interface
Autorise les moteurs de langage et les hôtes pour fournir la synchronisation des threads et mettre à jour le thread au débogage des informations d'état.  Cette interface étend l'interface d' `IRemoteDebugApplicationThread` pour fournir l'accès non distant au thread.  
  
 Outre les méthodes héritées de `IRemoteDebugApplicationThread`, l'interface `IDebugApplicationThread` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Fournit un mécanisme pour l'appel au code exécuté dans le thread d'application.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Détermine si ce thread est le thread en cours de exécution.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Détermine si ce thread est le thread du débogueur.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Définit la description de ce thread.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|Définit la description de l'état du thread.|