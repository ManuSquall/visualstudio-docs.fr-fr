---
title: IActiveScript::SetScriptState | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 58edef17fec1d94a09b327dff626658c42a273ba
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095028"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Place le moteur de script dans l’état donné. Cette méthode peut être appelée à partir de threads de base autre sans résultant dans une légende de base autre à des objets de l’hôte ou à la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ss`  
 [in] Définit le moteur de script à l’état donné. Peut prendre l’une des valeurs définies dans le [ScriptState, énumération](../../winscript/reference/scriptstate-enumeration.md) énumération.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_FAIL`|Le moteur de script ne prend pas en charge la transition vers l’état initialisé. L’hôte doit ignorer ce moteur de script et créer, initialiser et charger un nouveau moteur de script pour obtenir le même effet.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n'a pas encore été chargé ou initialisé) et par conséquent a échoué.|  
|`OLESCRIPT_S_PENDING`|La méthode a été en file d’attente avec succès, mais l’état n’a pas encore changé. Lorsque les modifications d’état, le site sera rappelé via le [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) (méthode).|  
|`S_FALSE`|La méthode a réussi, mais le script était déjà dans un état donné.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les États de moteur de script, consultez la section d’états de moteur de Script de [moteurs de Script Windows](../../winscript/windows-script-engines.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)