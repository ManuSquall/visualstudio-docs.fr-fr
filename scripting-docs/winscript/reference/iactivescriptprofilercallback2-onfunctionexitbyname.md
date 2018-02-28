---
title: IActiveScriptProfilerCallback2::OnFunctionExitByName | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionExitByName
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd26ab1cf36378c0f037d78a3c079c58e004006d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
Notifie le profileur à l’objet qui a le format du script du moteur terminé un appel de fonction de modèle DOM (Document Object) en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pwszFunctionName`  
 [in] Le nom de la fonction que le moteur de script terminée.  
  
 `scriptType`  
 [in] Le type de la fonction. Pour obtenir une description des valeurs valides, consultez [profiler_script_type, énumération](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## <a name="remarks"></a>Remarques  
 Pour les appels DOM, le moteur de script appelle cette méthode au lieu d’appeler [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md). Il s’agit en raison du grand nombre de méthodes et propriétés dans le DOM.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [Interface IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)