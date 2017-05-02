---
title: "IActiveScriptSiteDebugEx (interface) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteDebugEx (interface)"
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebugEx (interface)
Implémentez cette interface avec l'interface d' `IActiveScriptSiteDebug` si vous écrivez un hôte qui doit obtenir une notification d'une erreur d'exécution dans une application et éventuellement attacher à la demande de débogage.  Process Debug Manager fournit une notification via `IActiveScriptDebug` si un débogueur juste\-à\-temps de script est trouvé sur l'ordinateur.  Si aucun débogueur juste\-à\-temps de script n'est trouvé, le PDM fournit une notification via `IActiveScriptDebugEx` à la place.  
  
 Pour obtenir une notification d'une erreur d'exécution, votre hôte doit gérer [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/fr-fr/cf7639f9-a699-4571-9f3a-82ef52c0b5f4).  Selon une action utilisateur, vous pouvez ensuite décider d'attacher le débogueur et retourner internes, ou retourner le démarrage du débogueur dans le paramètre d'OnScriptErrorDebug `pfEnterDebugger` .  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Avertit l'hôte sur une erreur d'exécution du script lorsque Process Debug Manager ne recherche pas un débogueur juste\-à\-temps externe.|