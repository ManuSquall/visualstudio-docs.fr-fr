---
title: "IDebugSessionProvider, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugSessionProvider (interface)"
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSessionProvider, interface
L'interface principale fournie par un débogueur IDE pour activer l'hôte et le langage est initialisé le débogage.  Elle établit une session de débogage pour une application active.  Cette interface est implémentée par l'ordinateur de débogage le gestionnaire.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IDebugSessionProvider` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Initie une session de débogage avec l'application spécifiée.|