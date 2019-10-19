---
title: 'IActiveScriptProfilerCallback :: FunctionCompiled | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a17ce7548a6524df6911cdf952393020472b88ed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576472"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Avertit l’objet de profileur que le moteur de script a rencontré une fonction lors de la compilation d’un script.  
  
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
 dans ID unique de la fonction. Cet ID est assigné par le moteur de script.  
  
 `scriptId`  
 dans ID unique du script dont fait partie la fonction.  
  
 `pwszFunctionName`  
 dans Nom de la fonction, ou null pour une fonction anonyme.  
  
 `pwszFunctionNameHint`  
 dans Nom déduit de la fonction, ou null si le moteur de script ne déduit aucun nom.  
  
 `pIDebugDocumentContext`  
 dans S’il est disponible, pointeur vers une interface de `IUnknown` que le profileur doit interroger pour obtenir un pointeur d' [interface IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md) . Sinon, Null.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## <a name="remarks"></a>Notes  
 Le moteur de script peut fournir le contexte de document uniquement s’il est pris en charge par l’hôte.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)