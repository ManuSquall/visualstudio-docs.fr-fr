---
title: Interface IActiveScriptProfilerControl2 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2 interface
ms.assetid: 89455276-5c23-420b-a7e0-804a32635291
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7059868ae65c5093b24f342bd303ec70172171c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571532"
---
# <a name="iactivescriptprofilercontrol2-interface"></a>IActiveScriptProfilerControl2, interface
Fournit des méthodes qui ajoutent la possibilité de démarrer ou d’arrêter le profilage lorsqu’un script est en cours d’exécution.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|Notifie le profileur que vous avez commencé à profiler sur tous les moteurs de script applicables. Cela vous permet d’obtenir la pile des appels complète si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est en cours d’exécution lorsque vous démarrez le profilage.|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|Indique au profileur que vous allez arrêter le profilage sur tous les moteurs de script applicables. Cela vous permet d’obtenir la pile des appels complète si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est en cours d’exécution lorsque vous arrêtez le profilage.|  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)  
 [Interfaces de profiler de script actif](../../winscript/reference/active-script-profiler-interfaces.md)