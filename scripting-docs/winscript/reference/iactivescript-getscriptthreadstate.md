---
title: 'IActiveScript :: GetScriptThreadState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38f6ef4b0acdf6e3b746316bef8abe9a3f0f8225
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578010"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Récupère l’état actuel d’un thread de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `stidThread`  
 dans Identificateur du thread pour lequel l’État est souhaité, ou l’un des identificateurs de thread spéciaux suivants :  
  
|valeur|Signification|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Thread de base ; autrement dit, le thread dans lequel le moteur de script a été instancié.|  
|SCRIPTTHREADID_CURRENT|Thread en cours d’exécution.|  
  
 `pstsState`  
 à Adresse d’une variable qui reçoit l’état du thread indiqué. L’État est indiqué par l’une des valeurs de constantes nommées définies par l’énumération d' [énumération SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md) . Si ce paramètre n’identifie pas le thread actuel, l’État peut changer à tout moment.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n’a pas encore été chargé ou initialisé).|  
  
## <a name="remarks"></a>Notes  
 Cette méthode peut être appelée à partir de threads non de base sans aboutir à un appel de non-base pour héberger des objets ou à l’interface [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)