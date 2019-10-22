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
ms.openlocfilehash: 9ae520dcb36e00dfaba8702db6294a5a47484b0a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571712"
---
# <a name="iactivescriptprofilercallback-interface"></a>IActiveScriptProfilerCallback, interface
Fournit des méthodes qui sont utilisées par le moteur de script pour notifier un objet de profileur lorsque des événements se produisent. Cette interface est implémentée par l’objet de profileur.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Appelé pour initialiser l’objet de profileur chaque fois que le profilage est démarré sur un moteur de script.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Appelé pour libérer et libérer l’objet de profileur chaque fois que le profilage est arrêté sur un moteur de script.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Avertit l’objet de profileur que le moteur de script a compilé le script.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Avertit l’objet de profileur que le moteur de script a rencontré une fonction lors de la compilation d’un script.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Indique à l’objet de profileur que le moteur de script est sur le point d’exécuter un appel de fonction qui n’est pas un appel dans le Document Object Model (DOM).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Indique à l’objet de profileur que le moteur de script a terminé l’exécution d’un appel de fonction qui n’est pas un appel dans le DOM.|  
  
## <a name="remarks"></a>Notes  
 La notification des appels de fonction dans le Document Object Model (DOM) est fournie par l' [interface IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
> Pour ajouter la possibilité de démarrer et d’arrêter le profilage lorsqu’un script est en cours d’exécution, appelez les méthodes suivantes. À l’aide de ces méthodes, vous pouvez obtenir la pile des appels complète si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est en cours d’exécution lorsque vous démarrez ou arrêtez le profilage.  
> 
> - Appelez [IActiveScriptProfilerControl2 :: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) pour informer le profileur que vous avez démarré le profilage.  
>   - Appelez [IActiveScriptProfilerControl2 ::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) pour informer le profileur que vous allez bientôt arrêter le profilage.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de profiler de script actif](../../winscript/reference/active-script-profiler-interfaces.md)