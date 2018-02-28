---
title: IActiveScriptSiteDebugEx (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cf5849ff1fca282bace97774c6b7ac9e4510226
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx (interface)
Implémentez cette interface avec le `IActiveScriptSiteDebug` si vous écrivez un hôte qui a besoin pour obtenir une notification d’une erreur d’exécution dans une application et la possibilité de joindre à l’application pour le débogage de l’interface. Le Gestionnaire de déboguer des processus fournit une notification via `IActiveScriptDebug` si un juste-à-temps débogueur de script se trouve sur l’ordinateur. Si le débogueur de script sans juste-à-temps est trouvé, PDM fournit une notification via `IActiveScriptDebugEx` à la place.  
  
 Pour obtenir une notification d’une erreur d’exécution, votre hôte doit traiter [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/en-us/cf7639f9-a699-4571-9f3a-82ef52c0b5f4). En fonction de l’action de l’utilisateur, vous pouvez ensuite décider pour attacher le débogueur interne et le retour, ou pour retourner le démarrage du débogueur dans le OnScriptErrorDebug `pfEnterDebugger` paramètre.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Informe l’hôte sur une erreur d’exécution de script lorsque le processus de débogage Manager ne trouve pas un débogueur juste à temps externe.|