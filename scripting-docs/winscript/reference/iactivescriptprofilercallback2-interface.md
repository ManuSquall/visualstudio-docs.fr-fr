---
title: IActiveScriptProfilerCallback2 (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dc9fcd8ca4afec0fb474c0f3a7317b608c7c9f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback2-interface"></a>IActiveScriptProfilerCallback2, interface
Fournit des méthodes qui sont utilisées par le moteur de script pour notifier un objet de profileur lorsque surviennent des événements du modèle DOM (Document Object). Cette interface est implémentée par l’objet de profileur.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Notifie l’objet de profileur que le moteur de script va exécuter un appel de fonction DOM.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Notifie le profileur à l’objet que le format du script du moteur terminé un appel de fonction DOM en cours d’exécution.|  
  
## <a name="remarks"></a>Notes  
 Le `IActiveScriptProfilerCallback2` interface apparu avec Internet Explorer 9.  
  
 Notification des appels de fonction qui ne sont pas des appels dans le DOM est fournie par le [iactivescriptprofilercallback, Interface](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
>  Pour ajouter la possibilité de démarrer et arrêter le profilage lors de l’exécution d’un script, appelez les méthodes suivantes. À l’aide de ces méthodes, vous pouvez obtenir la pile des appels complète si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est en cours d’exécution lorsque vous démarrez ou arrêtez le profilage.  
>   
>  -   Appelez [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) pour informer le profileur que vous avez démarré le profilage.  
> -   Appelez [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) pour informer le profileur que vous serez bientôt arrêter le profilage.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de profiler de script actif](../../winscript/reference/active-script-profiler-interfaces.md)