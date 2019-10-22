---
title: 'IActiveScriptSite :: OnStateChange | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnStateChange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnStateChange
ms.assetid: 3e9c5cbe-ca8e-426a-84fd-04e9c2daac7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba8441d36f193f287dfec7406d5f136280c5a42e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570155"
---
# <a name="iactivescriptsiteonstatechange"></a>IActiveScriptSite::OnStateChange
Informe l’hôte que le moteur de script a modifié les États.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnStateChange(  
    SCRIPTSTATE ssScriptState  // new state of engine  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ssScriptState`  
 dans Valeur qui indique le nouvel État du script. Pour obtenir une description des États, consultez la méthode [IActiveScript :: GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) .  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)