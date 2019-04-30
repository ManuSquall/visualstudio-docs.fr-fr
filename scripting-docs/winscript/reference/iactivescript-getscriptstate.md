---
title: IActiveScript::GetScriptState | Microsoft Docs
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
ms.openlocfilehash: 0f9f3bedee9af9ae3cb145108d801f252267d5d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935746"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Récupère l’état actuel du moteur de script. Cette méthode peut être appelée à partir de threads de base autre sans résultant dans une légende de base autre à des objets de l’hôte ou à la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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