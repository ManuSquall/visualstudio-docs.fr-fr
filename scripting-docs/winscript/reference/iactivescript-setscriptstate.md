---
title: "IActiveScript::SetScriptState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.SetScriptState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_SetScriptState"
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::SetScriptState
Place le moteur de script dans l'état donné.  Cette méthode peut être appelée des threads non base sans ce qui provoque une légende non base des objets hôte ou à l'interface d' [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## Syntaxe  
  
```  
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### Paramètres  
 `ss`  
 \[in\]  Définit le moteur de script à l'état donné.  Peut avoir l'une des valeurs définies dans l'énumération de [SCRIPTSTATE, énumération](../../winscript/reference/scriptstate-enumeration.md) .  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|Succès.|  
|`E_FAIL`|Le moteur de script ne prend pas en charge la transition vers l'état initialisé.  L'hôte doit ignorer ce moteur de script et créer, démarrer, et charger un nouveau moteur de script pour accomplir la même effet.|  
|`E_UNEXPECTED`|L'appel à n'a pas été conçu \(par exemple, le moteur de script n'a pas encore été chargé ou n'a pas été initialisé\) et n'a pas été échoué par conséquent.|  
|`OLESCRIPT_S_PENDING`|La méthode a été mise en file d'attente avec succès, mais l'état n'a pas encore été modifiée.  En cas de modification de l'état, le site sont appelées arrières via la méthode d' [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .|  
|`S_FALSE`|La méthode réussit, mais le script est déjà dans l'état donné.|  
  
## Notes  
 Pour plus d'informations sur les rapports de moteur de script, afficher des rapports de moteur de script la section de [Windows Script, moteurs](../../winscript/windows-script-engines.md) .  
  
## Voir aussi  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)