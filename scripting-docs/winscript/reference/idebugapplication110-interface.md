---
title: "IDebugApplication110 (interface) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110 (interface)"
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplication110 (interface)
L'interface d' `IDebugApplication110` étend les fonctionnalités d' [IDebugApplication, interface](../../winscript/reference/idebugapplication-interface.md).  Vous pouvez obtenir une instance de cette interface en appelant QueryInterface sur une implémentation d' [IDebugApplication, interface](../../winscript/reference/idebugapplication-interface.md).  
  
> [!IMPORTANT]
>  Cette interface est implémentée par PDM v11.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Méthodes  
 L'interface `IDebugApplication110` expose les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|Effectue un appel synchrone sur le thread principal.|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|Effectue un appel asynchrone sur le thread principal.|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|Attend que les handles spécifiés l'un des rapports à tout en fournissant des appels de fibres transversale à publier sur ce thread.  Cette méthode doit être appelée à partir de le thread du débogueur.|