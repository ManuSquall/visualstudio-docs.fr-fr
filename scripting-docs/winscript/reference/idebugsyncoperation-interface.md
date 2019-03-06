---
title: Interface IDebugSyncOperation | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSyncOperation interface
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3724ad50771ca49460e130bf93ebc244681bd782
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349598"
---
# <a name="idebugsyncoperation-interface"></a>IDebugSyncOperation, interface
Permet d’extraire une opération (par exemple, d’évaluation de l’expression) qui doit être effectuée alors qu’imbriqué dans un thread bloqué particulier, un moteur de script. L’interface fournit également un mécanisme d’annulation des opérations qui ne répond pas.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugSyncOperation` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|Retourne le thread d’application cible pour cette opération synchrone.|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|Mode synchrone effectue l’opération et retourne.|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|Annule une opération en cours d’exécution sur un autre thread.|