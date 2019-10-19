---
title: 'IActiveScriptProfilerCallback :: OnFunctionExit | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionExit
apilocation:
- scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87801b7873e43498031264ff4719fb47eca99f40
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571670"
---
# <a name="iactivescriptprofilercallbackonfunctionexit"></a>IActiveScriptProfilerCallback::OnFunctionExit
Indique à l’objet de profileur que le moteur de script a terminé l’exécution d’un appel de fonction qui n’est pas un appel dans le Document Object Model (DOM).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `scriptId`  
 dans ID unique du script dont fait partie la fonction. Cet ID est assigné par le moteur de script.  
  
 `functionId`  
 dans ID unique de la fonction. Cet ID est assigné par le moteur de script.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## <a name="remarks"></a>Notes  
 Pour les appels DOM, le moteur de script appelle [IActiveScriptProfilerCallback2 :: OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) au lieu de `IActiveScriptProfilerCallback::OnFunctionExit`. Cela est dû au grand nombre de méthodes et de propriétés uniques dans le DOM.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptProfilerCallback :: OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)    
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)