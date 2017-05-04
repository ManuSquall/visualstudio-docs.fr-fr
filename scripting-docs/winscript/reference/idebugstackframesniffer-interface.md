---
title: "IDebugStackFrameSniffer, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrameSniffer (interface)"
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSniffer, interface
Permet d'énumérer les frames de pile logiques connus par un composant.  Les moteurs de script implémentent généralement cette interface.  Le processus de débogage utilise de gestionnaire cette interface pour rechercher tous les frames de pile associés à un thread donné.  
  
> [!NOTE]
>  Le débogueur appelle cette interface du thread concerné.  Le moteur de script doit identifier le thread actuel et retourner un énumérateur approprié.  
  
## Méthodes  
 Outre les méthodes héritées de `IUnknown`, l'interface `IDebugStackFrameSniffer` expose les méthodes suivantes.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Retourne un énumérateur des frames de pile du thread actuel.|