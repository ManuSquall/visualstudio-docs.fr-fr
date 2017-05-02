---
title: "SCRIPTTHREADID, constantes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTTHREADID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTTHREADID"
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# SCRIPTTHREADID, constantes
Utilisé pour spécifier le type de thread.  
  
## Syntaxe  
  
```  
typedef DWORD SCRIPTTHREADID;  
```  
  
## Constantes  
  
|Constante|Valeur|Signification|  
|---------------|------------|-------------------|  
|SCRIPTTHREADID\_CURRENT|0xFFFFFFFD|Le thread en cours.|  
|SCRIPTTHREADID\_BASE|0xFFFFFFFE|Le thread de base ; autrement dit, le thread dans lequel le moteur de script a été instancié.|  
|SCRIPTTHREADID\_ALL|0xFFFFFFFF|Tous les threads.|  
  
## Notes  
 Le type d' `SCRIPTTHREADID` est utilisé par `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`, et `IActiveScript::InterruptScriptThread`, mais les constantes peuvent être utilisées par `IActiveScript::GetScriptThreadState` et `IActiveScript::InterruptScriptThread`.  
  
## Voir aussi  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)