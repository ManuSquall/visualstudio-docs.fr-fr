---
title: "IActiveScriptProfilerControl, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptProfilerControl, interface
Implémentée par le moteur de script qui prend en charge le profilage.  En général, un objet qui implémente `IActiveScriptProfilerControl` également implémente l'interface d' [IActiveScript](../../winscript/reference/iactivescript.md) .  Dans ce cas, vous pouvez obtenir un handle vers l'interface d' `IActiveScriptProfilerControl` en appelant la méthode d' `IUnknown::QueryInterface` sur l'objet.  L'interface fournit les méthodes nécessaires pour arrêter et démarrer le profilage sur le moteur de script.  
  
## Méthodes  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Démarre le profilage sur le moteur de script.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Définit le masque de profileur dans le moteur de script.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Arrête le profilage sur le moteur de script.|  
  
## Voir aussi  
 [Profilage de script actif, interfaces](../../winscript/reference/active-script-profiler-interfaces.md)