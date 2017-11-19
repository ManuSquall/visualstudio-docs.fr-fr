---
title: IActiveScriptProfilerCallback::OnFunctionExit | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.OnFunctionExit
apilocation: scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57a3343c7e3747c48a4c43a1c1ac17fe6502aee3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackonfunctionexit"></a>IActiveScriptProfilerCallback::OnFunctionExit
Notifie le profileur à l’objet qui d’appeler le moteur de script terminé l’exécution d’une fonction qui n’est pas un appel dans le modèle DOM (Document Object).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnFunctionExit(  
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
 Pour les appels DOM, le moteur de script appelle [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) au lieu de `IActiveScriptProfilerCallback::OnFunctionExit`. Il s’agit en raison du grand nombre de méthodes et propriétés dans le DOM.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)   
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)