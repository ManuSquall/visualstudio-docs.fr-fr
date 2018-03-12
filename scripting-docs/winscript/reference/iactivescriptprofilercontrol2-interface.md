---
title: IActiveScriptProfilerControl2 (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2 interface
ms.assetid: 89455276-5c23-420b-a7e0-804a32635291
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9bc0dfa31b37a6bf99427c8eddfe2bd038da9b9d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol2-interface"></a>IActiveScriptProfilerControl2, interface
Fournit des méthodes qui ajoutent la possibilité de démarrer ou arrêter le profilage lors de l’exécution d’un script.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|Notifie le profileur que vous avez démarré le profilage sur tous les moteurs de script applicables. Cela vous permet d’obtenir la pile des appels complète si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est en cours d’exécution lorsque vous démarrez le profilage.|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|Notifie le profileur que vous vous apprêtez à arrêter le profilage sur tous les moteurs de script applicables. Cela vous permet d’obtenir la pile des appels complète si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est en cours d’exécution lorsque vous arrêtez le profilage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Iactivescriptprofilercontrol, Interface](../../winscript/reference/iactivescriptprofilercontrol-interface.md)   
 [Interfaces de profiler de script actif](../../winscript/reference/active-script-profiler-interfaces.md)