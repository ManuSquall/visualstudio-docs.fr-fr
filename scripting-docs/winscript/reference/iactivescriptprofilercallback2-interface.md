---
title: Interface IActiveScriptProfilerCallback2 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25f9616497192659df67feedfe16bd9ea0c5e3b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577300"
---
# <a name="iactivescriptprofilercallback2-interface"></a>IActiveScriptProfilerCallback2, interface
Fournit des méthodes utilisées par le moteur de script pour notifier un objet de profileur lorsque des événements Document Object Model (DOM) se produisent. Cette interface est implémentée par l’objet de profileur.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Indique à l’objet de profileur que le moteur de script va exécuter un appel de fonction DOM.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Indique à l’objet de profileur que le moteur de script a terminé l’exécution d’un appel de fonction DOM.|  
  
## <a name="remarks"></a>Notes  
 Interface `IActiveScriptProfilerCallback2` publiée pour la première fois avec Internet Explorer 9.  
  
 La notification d’appels de fonction qui n’appellent pas le DOM est fournie par l' [interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
> Pour ajouter la possibilité de démarrer et d’arrêter le profilage lorsqu’un script est en cours d’exécution, appelez les méthodes suivantes. À l’aide de ces méthodes, vous pouvez obtenir la pile des appels complète si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est en cours d’exécution lorsque vous démarrez ou arrêtez le profilage.  
> 
> - Appelez [IActiveScriptProfilerControl2 :: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) pour informer le profileur que vous avez démarré le profilage.  
>   - Appelez [IActiveScriptProfilerControl2 ::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) pour informer le profileur que vous allez bientôt arrêter le profilage.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de profiler de script actif](../../winscript/reference/active-script-profiler-interfaces.md)