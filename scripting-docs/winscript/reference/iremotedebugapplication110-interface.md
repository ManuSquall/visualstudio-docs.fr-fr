---
title: Interface IRemoteDebugApplication110 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110 Interface
ms.assetid: 785ab46a-8827-41cb-806a-132e6b2c8f47
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f280e2b869a3046ecb2d3fac37facdcc1bfeb7fb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349879"
---
# <a name="iremotedebugapplication110-interface"></a>IRemoteDebugApplication110 (interface)
Utilisé pour fournir de nouvelles capacités qui peuvent être appelées par les débogueurs de script et des appelants in-process.  
  
> [!IMPORTANT]
>  Elle est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="methods"></a>Méthodes  
 L'interface `IRemoteDebugApplication110` expose les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[IRemoteDebugApplication110::SetDebuggerOptions](../../winscript/reference/iremotedebugapplication110-setdebuggeroptions.md)|Appelée pour mettre à jour les options du débogueur. L’options par défaut, 0 (SDO_NONE).|  
|[IRemoteDebugApplication110::GetCurrentDebuggerOptions](../../winscript/reference/iremotedebugapplication110-getcurrentdebuggeroptions.md)|Retourne l’ensemble actuel des options qui sont activées.|  
|[IRemoteDebugApplication110::GetMainThread](../../winscript/reference/iremotedebugapplication110-getmainthread.md)|Retourne le thread principal pour les ordinateurs hôtes qui appellent SetSite.|