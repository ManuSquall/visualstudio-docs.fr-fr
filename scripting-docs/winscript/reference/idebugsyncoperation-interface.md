---
title: "IDebugSyncOperation, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugSyncOperation (interface)"
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation, interface
Permet à un moteur de script pour abréger une opération \(telle que l'évaluation de l'expression\) qui doit être exécuté tandis que imbriqué dans un thread bloqué particulier.  L'interface fournit également un mécanisme d'annulation des opérations insensibles.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IDebugSyncOperation` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|Retourne le thread cible d'application pour ce test synchrone.|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|Exécute de façon synchrone l'exécution et retourne.|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|Annule une exécution en cours sur un autre thread.|