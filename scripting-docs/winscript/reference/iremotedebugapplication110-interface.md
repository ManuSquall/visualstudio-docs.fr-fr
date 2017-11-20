---
title: IRemoteDebugApplication110 (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IRemoteDebugApplication110 Interface
ms.assetid: 785ab46a-8827-41cb-806a-132e6b2c8f47
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d384cea22b79b2a7ca9af3424d053fb3062d79a3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplication110-interface"></a>IRemoteDebugApplication110 (interface)
Utilisé pour fournir les nouvelles fonctionnalités qui peuvent être appelées par les débogueurs de script et des appelants dans le processusent.  
  
> [!IMPORTANT]
>  Elle est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="methods"></a>Méthodes  
 L'interface `IRemoteDebugApplication110` expose les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[IRemoteDebugApplication110::SetDebuggerOptions](../../winscript/reference/iremotedebugapplication110-setdebuggeroptions.md)|Appelé pour mettre à jour les options du débogueur. L’options par défaut, 0 (SDO_NONE).|  
|[IRemoteDebugApplication110::GetCurrentDebuggerOptions](../../winscript/reference/iremotedebugapplication110-getcurrentdebuggeroptions.md)|Retourne l’ensemble actuel des options qui sont activées.|  
|[IRemoteDebugApplication110::GetMainThread](../../winscript/reference/iremotedebugapplication110-getmainthread.md)|Retourne le thread principal pour les ordinateurs hôtes qui appellent SetSite.|