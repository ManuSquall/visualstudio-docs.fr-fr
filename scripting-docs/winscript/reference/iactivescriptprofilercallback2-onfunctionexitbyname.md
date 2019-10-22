---
title: 'IActiveScriptProfilerCallback2 :: OnFunctionExitByName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a70bc72dd1070759ad8b78e43926f06a2c56ec15
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571624"
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
Indique à l’objet de profileur que le moteur de script a terminé l’exécution d’un appel de fonction Document Object Model (DOM).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pwszFunctionName`  
 dans Nom de la fonction que le moteur de script a terminé d’exécuter.  
  
 `scriptType`  
 dans Type de la fonction. Pour obtenir une description des valeurs valides, consultez [énumération PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## <a name="remarks"></a>Notes  
 Pour les appels DOM, le moteur de script appelle cette méthode au lieu d’appeler [IActiveScriptProfilerCallback :: OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md). Cela est dû au grand nombre de méthodes et de propriétés uniques dans le DOM.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptProfilerCallback2 :: OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)    
 [Interface IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)