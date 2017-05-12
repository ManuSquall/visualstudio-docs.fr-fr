---
title: "IRemoteDebugApplication110 (interface) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110 (interface)"
ms.assetid: 785ab46a-8827-41cb-806a-132e6b2c8f47
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IRemoteDebugApplication110 (interface)
Utilisé pour fournir de nouvelles fonctionnalités qui peuvent être appelées par des débogueurs de script et des appelants in\-process.  
  
> [!IMPORTANT]
>  Cette interface est implémentée par PDM v11.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Méthodes  
 L'interface `IRemoteDebugApplication110` expose les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IRemoteDebugApplication110::SetDebuggerOptions](../../winscript/reference/iremotedebugapplication110-setdebuggeroptions.md)|Appelée pour mettre à jour des options de débogueur.  La valeur par défaut d'options à 0 \(SDO\_NONE\).|  
|[IRemoteDebugApplication110::GetCurrentDebuggerOptions](../../winscript/reference/iremotedebugapplication110-getcurrentdebuggeroptions.md)|Retourne le jeu actuel d'options qui sont activées.|  
|[IRemoteDebugApplication110::GetMainThread](../../winscript/reference/iremotedebugapplication110-getmainthread.md)|Retourne le thread principal pour les hôtes qui appellent SetSite.|