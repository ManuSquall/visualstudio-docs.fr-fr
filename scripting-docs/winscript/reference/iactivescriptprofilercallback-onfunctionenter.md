---
title: IActiveScriptProfilerCallback::OnFunctionEnter | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.OnFunctionEnter
apilocation: scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9af9dc5ce1f4cb0eb5c328c90c20184111afd9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
Notifie l’objet de profileur que le moteur de script est prêt à exécuter un appel de fonction qui n’est pas un appel dans le modèle DOM (Document Object).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnFunctionEnter(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `scriptId`  
 [in] ID unique du script faisant partie de la fonction. Cet ID est assigné par le moteur de script.  
  
 `functionId`  
 [in] ID unique de la fonction. Cet ID est assigné par le moteur de script.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## <a name="remarks"></a>Remarques  
 Pour les appels DOM, le moteur de script appelle [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) au lieu de `IActiveScriptProfilerCallback::OnFunctionEnter`. Il s’agit en raison du grand nombre de méthodes et propriétés dans le DOM.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)