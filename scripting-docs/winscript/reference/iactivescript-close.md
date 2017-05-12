---
title: "IActiveScript::Close | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.Close
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_Close"
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::Close
Fait pour abandonner tout script actuellement chargé, pour détruire son état, et pour libérer le moteur de script tous les pointeurs d'interface qu'elle doit d'autres objets, ainsi entrant un état fermé.  Les récepteurs d'événements, le texte immédiatement l'exécution du script, et les macros appels qui sont déjà en cours sont effectués avant les modifications d'état \(utilisation [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) d'annuler un thread en cours de exécution du script\).  Cette méthode doit être appelée par l'hôte de création avant que l'interface est libérée pour empêcher les problèmes de référence circulaire.  
  
## Syntaxe  
  
```  
HRESULT Close(void);  
```  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur|Signification|  
|------------|-------------------|  
|`S_OK`|Succès.|  
|`E_UNEXPECTED`|L'appel à n'a pas été conçu \(par exemple, le moteur de script est déjà dans l'état fermé.\)|  
|`OLESCRIPT_S_PENDING`|La méthode a été mise en file d'attente avec succès, mais l'état n'a pas encore été modifiée.  En cas de modification de l'état, le site doit être appelées arrière sur la méthode d' [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .|  
|`S_FALSE`|La méthode réussit, mais le script a déjà été fermée.|  
  
## Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)