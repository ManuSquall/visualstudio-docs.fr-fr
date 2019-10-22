---
title: 'IActiveScriptProfilerCallback :: ScriptCompiled | Microsoft Docs'
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
ms.openlocfilehash: f7252134fc86bfd63b74a181b18327212a1b2dc1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571661"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Avertit l’objet de profileur que le moteur de script a compilé un script. Cette méthode est appelée pour chaque script compilé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `scriptId`  
 dans ID unique du script qui a été compilé. Cet ID est assigné par le moteur de script.  
  
 `type`  
 dans Type du script qui a été compilé. Les valeurs sont définies dans l' [énumération PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 dans S’il est disponible, pointeur vers une interface de `IUnknown` que le profileur doit interroger pour obtenir un pointeur d' [interface IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md) . Dans le cas contraire, la valeur est null.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## <a name="remarks"></a>Notes  
 Le moteur de script peut fournir le contexte de document uniquement s’il est pris en charge par l’hôte.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)