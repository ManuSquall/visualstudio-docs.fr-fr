---
title: IActiveScriptProfilerCallback::ScriptCompiled | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.ScriptCompiled
apilocation:
- scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a198667e7dc30969c32b556620b139d52f833543
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993233"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Notifie le profileur à l’objet du moteur de script compilé un script. Cette méthode est appelée pour chaque script qui est compilé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `scriptId`  
 [in] ID unique du script qui a été compilé. Cet ID est attribué par le moteur de script.  
  
 `type`  
 [in] Le type du script qui a été compilé. Les valeurs sont définies dans [profiler_script_type, énumération](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 [in] S’il est disponible, un pointeur vers un `IUnknown` interface que le profileur doit interroger pour un [IDebugDocumentContext (Interface)](../../winscript/reference/idebugdocumentcontext-interface.md) pointeur. Sinon, ce sera null.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## <a name="remarks"></a>Notes  
 Le moteur de script peut fournir le contexte de document uniquement si cela est pris en charge par l’hôte.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)