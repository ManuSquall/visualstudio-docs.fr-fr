---
title: IActiveScriptProfilerCallback::FunctionCompiled | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.FunctionCompiled
apilocation:
- scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4bd032914605c61b13a0a56a42e510c2af252f7e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091401"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Notifie le profileur à l’objet du moteur de script a rencontré une fonction lors de la compilation d’un script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `functionId`  
 [in] ID unique de la fonction. Cet ID est attribué par le moteur de script.  
  
 `scriptId`  
 [in] ID unique du script faisant partie de la fonction.  
  
 `pwszFunctionName`  
 [in] Le nom de la fonction, ou null pour une fonction anonyme.  
  
 `pwszFunctionNameHint`  
 [in] Le nom de la fonction, ou null si le moteur de script ne déduit pas n’importe quel nom déduit.  
  
 `pIDebugDocumentContext`  
 [in] S’il est disponible, le pointeur vers un `IUnknown` interface que le profileur doit interroger pour un [IDebugDocumentContext (Interface)](../../winscript/reference/idebugdocumentcontext-interface.md) pointeur. Sinon, Null.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## <a name="remarks"></a>Notes  
 Le moteur de script peut fournir le contexte de document uniquement si cela est pris en charge par l’hôte.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)