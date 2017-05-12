---
title: "IDebugThreadCall, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugThreadCall (interface)"
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugThreadCall, interface
L'interface d' `IDebugThreadCall` est généralement implémentée par un composant qui effectue des appels inter\-threads avec `IDebugThread` collectant l'implémentation fournie par le processus à déboguer le gestionnaire \(PDM\).  
  
 Le PDM appelle l'interface d' `IDebugThreadCall` dans le thread désiré, et l'interface d' `IDebugThreadCall` distribue l'appel de l'implémentation souhaitée.  L'interface d' `IDebugThreadCall` effectue les informations de paramètre passées dans les paramètres au niveau approprié.  
  
 l'interface d' `IDebugThreadCall` est un objet libre de threads.  
  
## Méthodes  
 Outre les méthodes héritées de `IUnknown`, l'interface `IDebugThreadCall` expose les méthodes suivantes.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Appels de handles pour exécuter du code dans un autre thread.|