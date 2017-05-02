---
title: "IDebugStackFrameSnifferEx, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrameSnifferEx (interface)"
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSnifferEx, interface
Permet d'énumérer les frames de pile logiques connus par un composant.  Les moteurs de script implémentent généralement cette interface.  Le processus de débogage utilise de gestionnaire cette interface pour rechercher tous les frames de pile associés à un thread donné.  
  
> [!NOTE]
>  Cette interface est appelée du thread concerné.  L'implémentation de l'interface doit identifier le thread actuel et retourner un énumérateur approprié.  
  
 Outre les méthodes héritées de `IDebugStackFrameSniffer`, l'interface `IDebugStackFrameSnifferEx` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Retourne un énumérateur des frames de pile du thread actuel.|