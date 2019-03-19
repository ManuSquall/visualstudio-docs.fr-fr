---
title: Interface IActiveScriptProfilerCallback | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0eb8ef209e1fc55fabf37c0c4469fd390f5a478
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146329"
---
# <a name="iactivescriptprofilercallback-interface"></a>IActiveScriptProfilerCallback, interface
Fournit des méthodes qui sont utilisées par le moteur de script pour signaler un objet de profileur événements se produisent. Cette interface est implémentée par l’objet de profileur.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Appelée pour initialiser l’objet de profileur chaque fois que le profilage est démarré sur un moteur de script.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Appelée pour libérer et de libérer l’objet de profileur chaque fois que le profilage est arrêté sur un moteur de script.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Notifie le profileur à l’objet du moteur de script compilé le script.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Notifie le profileur à l’objet du moteur de script a rencontré une fonction lors de la compilation d’un script.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Avertit l’objet de profileur que le moteur de script est prêt à exécuter un appel de fonction qui n’est pas un appel dans le modèle DOM (Document Object).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Notifie le profileur d’objet que le moteur de script terminé l’exécution d’une fonction appeler qui n’est pas un appel dans le DOM.|  
  
## <a name="remarks"></a>Notes  
 Notification des appels de fonction dans le modèle DOM (Document Object) est fournie par le [IActiveScriptProfilerCallback2 (Interface)](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
>  Pour ajouter la possibilité de démarrer et arrêter le profilage lors de l’exécution d’un script, appelez les méthodes suivantes. À l’aide de ces méthodes, vous pouvez obtenir la pile des appels complète si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est en cours d’exécution lorsque vous démarrez ou arrêtez le profilage.  
> 
> - Appelez [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) pour informer le profileur que vous avez démarré le profilage.  
>   -   Appelez [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) pour informer le profileur que vous serez bientôt arrêter le profilage.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de profiler de script actif](../../winscript/reference/active-script-profiler-interfaces.md)