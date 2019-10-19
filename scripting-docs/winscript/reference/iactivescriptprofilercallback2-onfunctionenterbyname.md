---
title: 'IActiveScriptProfilerCallback2 :: OnFunctionEnterByName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionEnterByName
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0407441c77250b2cc27e9fee09c5039bb8e44ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571641"
---
# <a name="iactivescriptprofilercallback2onfunctionenterbyname"></a>IActiveScriptProfilerCallback2::OnFunctionEnterByName
Indique à l’objet de profileur que le moteur de script va exécuter un appel de fonction Document Object Model (DOM).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pwszFunctionName`  
 dans Nom de la fonction que le moteur de script va exécuter.  
  
 `scriptType`  
 dans Type de la fonction. Pour obtenir une description des valeurs valides, consultez [énumération PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## <a name="remarks"></a>Notes  
 Pour les appels DOM, le moteur de script appelle cette méthode au lieu d’appeler [IActiveScriptProfilerCallback :: OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md). Cela est dû au grand nombre de méthodes et de propriétés uniques dans le DOM.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptProfilerCallback2 :: OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)    
 [Interface IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)