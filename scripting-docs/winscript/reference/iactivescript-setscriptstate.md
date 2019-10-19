---
title: 'IActiveScript :: SetScriptState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptState
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea947e00ffd5a3498261f4a3a8acd4791e8ace60
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577987"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Place le moteur de script dans l’État donné. Cette méthode peut être appelée à partir de threads non de base sans aboutir à un appel de non-base pour héberger des objets ou à l’interface [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ss`  
 dans Définit le moteur de script à l’État donné. Il peut s’agir de l’une des valeurs définies dans l’énumération d' [énumération SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md) .  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_FAIL`|Le moteur de script ne prend pas en charge la transition vers l’état initialisé. L’hôte doit ignorer ce moteur de script et créer, initialiser et charger un nouveau moteur de script pour obtenir le même effet.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n’a pas encore été chargé ou initialisé) et par conséquent a échoué.|  
|`OLESCRIPT_S_PENDING`|La méthode a été mise en file d’attente avec succès, mais l’État n’a pas encore changé. Lorsque l’état change, le site est rappelé par la méthode [IActiveScriptSite :: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .|  
|`S_FALSE`|La méthode a réussi, mais le script était déjà dans l’État donné.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les États du moteur de script, consultez la section États du moteur de script des [moteurs de script Windows](../../winscript/windows-script-engines.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript :: clone](../../winscript/reference/iactivescript-clone.md)    
 [IActiveScript :: GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)    
 [IActiveScript :: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)    
 [IActiveScriptParse ::P arsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md)    
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)