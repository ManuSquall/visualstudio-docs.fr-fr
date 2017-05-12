---
title: "IDebugSessionProviderEx, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugSessionProviderEx, interface
L'interface principale a fourni par un débogueur IDE pour activer le serveur et LINQ a initialisé le débogage.  Elle établit une session de débogage pour une application active.  Cette interface est implémentée par Debug Machine Manager.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IDebugSessionProviderEx` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Détermine si le débogage juste\-à\-temps est possible avec l'application spécifiée.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Initie une session de débogage avec l'application spécifiée.|