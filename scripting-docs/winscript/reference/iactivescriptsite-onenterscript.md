---
title: "IActiveScriptSite::OnEnterScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnEnterScript
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnEnterScript"
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnEnterScript
Signale à l'hôte que le moteur de script a démarré l'exécution du code de script.  
  
## Syntaxe  
  
```  
HRESULT OnEnterScript(void);  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  
  
## Notes  
 Le moteur de script doit appeler cette méthode sur chaque entrée ou rentrée dans le moteur de script.  Par exemple, si le script appelle un objet qui déclenche ensuite un événement géré par le moteur de script, le moteur de script doit appeler `IActiveScriptSite::OnEnterScript` avant d'exécuter l'événement, et doit appeler la méthode d' [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) après avoir exécuté l'événement mais avant le retour à l'objet qui a déclenché l'événement.  Les appels à cette méthode peuvent être imbriqués.  Chaque appel à cette méthode requiert un appel correspondant à `IActiveScriptSite::OnLeaveScript`.  
  
## Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)