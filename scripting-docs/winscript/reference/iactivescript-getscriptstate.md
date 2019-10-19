---
title: 'IActiveScript :: GetScriptState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d266e713879aafe1c5ca271d46b3030f3275460f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575736"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Récupère l’état actuel du moteur de script. Cette méthode peut être appelée à partir de threads non de base sans aboutir à un appel de non-base pour héberger des objets ou à l’interface [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pss`  
 à Adresse d’une variable qui reçoit une valeur définie dans l’énumération d' [énumération SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md) . La valeur indique l’état actuel du moteur de script associé au thread appelant.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_POINTER` si un pointeur non valide a été spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)