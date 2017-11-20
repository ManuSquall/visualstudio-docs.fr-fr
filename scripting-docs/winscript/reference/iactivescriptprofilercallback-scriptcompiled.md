---
title: IActiveScriptProfilerCallback::ScriptCompiled | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.ScriptCompiled
apilocation: scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ea1823087b323f2acc9b87edfce48bbe9f924bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Notifie le profileur à l’objet de moteur de script compilé un script. Cette méthode est appelée pour chaque script qui est compilé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `scriptId`  
 [in] ID unique du script qui a été compilé. Cet ID est assigné par le moteur de script.  
  
 `type`  
 [in] Le type du script qui a été compilé. Les valeurs sont définies dans [profiler_script_type, énumération](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 [in] S’il est disponible, un pointeur vers un `IUnknown` interface que le profileur doit interroger pour un [idebugdocumentcontext, Interface](../../winscript/reference/idebugdocumentcontext-interface.md) pointeur. Dans le cas contraire, il sera null.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## <a name="remarks"></a>Remarques  
 Le moteur de script peut fournir le contexte de document uniquement si cela est pris en charge par l’hôte.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)