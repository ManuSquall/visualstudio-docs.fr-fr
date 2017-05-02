---
title: "IActiveScriptSite::OnLeaveScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnLeaveScript
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnLeaveScript"
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnLeaveScript
Signale à l'hôte que le moteur de script retournées d'exécuter le code de script.  
  
## Syntaxe  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  
  
## Notes  
 Le moteur de script doit appeler cette méthode avant de retourner le contrôle à une application appelante qui est entrée dans le moteur de script.  Par exemple, si le script appelle un objet qui déclenche ensuite un événement géré par le moteur de script, le moteur de script doit appeler la méthode d' [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) avant d'exécuter l'événement, et doit appeler `IActiveScriptSite::OnLeaveScript` après avoir exécuté l'événement avant le retour à l'objet qui a déclenché l'événement.  Les appels à cette méthode peuvent être imbriqués.  Chaque appel à `IActiveScriptSite::OnEnterScript` requiert un appel correspondant à cette méthode.  
  
## Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)