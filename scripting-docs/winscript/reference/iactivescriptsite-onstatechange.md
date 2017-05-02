---
title: "IActiveScriptSite::OnStateChange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnStateChange
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnStateChange"
ms.assetid: 3e9c5cbe-ca8e-426a-84fd-04e9c2daac7e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSite::OnStateChange
Signale à l'hôte que le moteur de script a modifié des rapports.  
  
## Syntaxe  
  
```  
HRESULT OnStateChange(  
    SCRIPTSTATE ssScriptState  // new state of engine  
);  
```  
  
#### Paramètres  
 `ssScriptState`  
 \[in\]  Évaluez qui indique l'état de script.  Consultez la méthode d' [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) pour une description des rapports.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  
  
## Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)