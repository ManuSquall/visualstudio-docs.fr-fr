---
title: IEnumRemoteDebugApplicationThreads Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumRemoteDebugApplicationThreads interface
ms.assetid: 4ae6f8ef-e7be-4e2d-9be4-e0cde0a70eb1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d57e945593641036bbfbbecc90b790251c12075f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62807210"
---
# <a name="ienumremotedebugapplicationthreads-interface"></a>IEnumRemoteDebugApplicationThreads, interface
Énumère les threads en cours d’exécution dans une application.  
  
 Outre les méthodes héritées de `IUnknown`, le `IEnumRemoteDebugApplicationThreads` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IEnumRemoteDebugApplicationThreads::Next](../../winscript/reference/ienumremotedebugapplicationthreads-next.md)|Récupère un nombre spécifié de segments dans une séquence d’énumération.|  
|[IEnumRemoteDebugApplicationThreads::Skip](../../winscript/reference/ienumremotedebugapplicationthreads-skip.md)|Ignore un nombre spécifié de segments dans une séquence d’énumération.|  
|[IEnumRemoteDebugApplicationThreads::Reset](../../winscript/reference/ienumremotedebugapplicationthreads-reset.md)|Réinitialise une séquence d’énumération au début.|  
|[IEnumRemoteDebugApplicationThreads::Clone](../../winscript/reference/ienumremotedebugapplicationthreads-clone.md)|Crée un énumérateur qui contient le même état que l’énumérateur en cours.|