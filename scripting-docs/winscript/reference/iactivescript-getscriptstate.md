---
title: "IActiveScript::GetScriptState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptState"
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetScriptState
Récupère l'état actuel du moteur de script.  Cette méthode peut être appelée des threads non base sans ce qui provoque une légende non base des objets hôte ou à l'interface d' [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## Syntaxe  
  
```  
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### Paramètres  
 `pss`  
 \[out\]  L'adresse d'une variable qui accepte une valeur définie dans l'énumération de [SCRIPTSTATE, énumération](../../winscript/reference/scriptstate-enumeration.md) .  La valeur indique l'état actuel du moteur de script associé au thread appelant.  
  
## Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_POINTER` si un pointeur non valide a été spécifié.  
  
## Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)