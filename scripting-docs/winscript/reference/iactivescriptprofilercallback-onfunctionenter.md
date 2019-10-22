---
title: 'IActiveScriptProfilerCallback :: OnFunctionEnter | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionEnter
apilocation:
- scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6157638353712d6f376fa1eb46a68980b493a5c3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571688"
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
Indique à l’objet de profileur que le moteur de script est sur le point d’exécuter un appel de fonction qui n’est pas un appel dans le Document Object Model (DOM).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnFunctionEnter(  
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
 Pour les appels DOM, le moteur de script appelle [IActiveScriptProfilerCallback2 :: OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) au lieu de `IActiveScriptProfilerCallback::OnFunctionEnter`. Cela est dû au grand nombre de méthodes et de propriétés uniques dans le DOM.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptProfilerCallback :: OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)    
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)