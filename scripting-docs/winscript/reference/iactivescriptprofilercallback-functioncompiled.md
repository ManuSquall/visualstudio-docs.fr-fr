---
title: IActiveScriptProfilerCallback::FunctionCompiled | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.FunctionCompiled
apilocation: scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 797476d4892224ad0b27c9caf579c0704693c835
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Notifie le profileur à l’objet de moteur de script a rencontré une fonction lors de la compilation d’un script.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `functionId`  
 [in] ID unique de la fonction. Cet ID est assigné par le moteur de script.  
  
 `scriptId`  
 [in] ID unique du script faisant partie de la fonction.  
  
 `pwszFunctionName`  
 [in] Le nom de la fonction, ou null pour une fonction anonyme.  
  
 `pwszFunctionNameHint`  
 [in] Nom de la fonction, ou null si le moteur de script ne reconnaît pas de n’importe quel nom déduit.  
  
 `pIDebugDocumentContext`  
 [in] S’il est disponible, le pointeur vers un `IUnknown` interface que le profileur doit interroger pour un [idebugdocumentcontext, Interface](../../winscript/reference/idebugdocumentcontext-interface.md) pointeur. Sinon, Null.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## <a name="remarks"></a>Remarques  
 Le moteur de script peut fournir le contexte de document uniquement si cela est pris en charge par l’hôte.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)