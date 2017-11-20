---
title: IActiveScript::GetScriptState | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetScriptState
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 285a09308c7477dbeed68f9f93417b503ca4fe49
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Récupère l’état actuel du moteur de script. Cette méthode peut être appelée à partir de threads de l’autre base sans résultant dans une légende de l’autre base d’héberger des objets ou à la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pss`  
 [out] Adresse d’une variable qui reçoit une valeur définie dans le [ScriptState, énumération](../../winscript/reference/scriptstate-enumeration.md) énumération. La valeur indique l’état actuel du moteur de script associé au thread appelant.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_POINTER` si un pointeur non valide a été spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)