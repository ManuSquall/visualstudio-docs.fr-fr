---
title: IActiveScriptProfilerCallback2::OnFunctionExitByName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionExitByName
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb198f56e5ff73561fe7b42a25b019dfb0e3817c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094560"
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
Notifie le profileur à l’objet du moteur de script terminé d’exécuter un appel de fonction de modèle DOM (Document Object).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pwszFunctionName`  
 [in] Le nom de la fonction que le moteur de script terminé en cours d’exécution.  
  
 `scriptType`  
 [in] Le type de la fonction. Pour obtenir une description des valeurs valides, consultez [profiler_script_type, énumération](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## <a name="remarks"></a>Notes  
 Pour les appels de DOM, le moteur de script appelle cette méthode au lieu d’appeler [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md). Il s’agit en raison du grand nombre de méthodes uniques et des propriétés dans le DOM.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [Interface IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)