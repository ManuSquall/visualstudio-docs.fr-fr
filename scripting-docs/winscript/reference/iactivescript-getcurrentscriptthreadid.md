---
title: "IActiveScript::GetCurrentScriptThreadID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetCurrentScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetCurrentScriptThreadID"
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetCurrentScriptThreadID
Récupère un identificateur script\-engine\- défini pour le thread en cours.  L'identificateur peut être utilisé dans les appels suivants aux méthodes d'exécution\- contrôle de thread de script telles que la méthode d' [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
## Syntaxe  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### Paramètres  
 `pstidThread`  
 \[out\]  L'adresse d'une variable qui accepte l'identificateur du thread de script est associé au thread actuel.  La traduction de cet identificateur est laissée au moteur de script, mais elle peut être une seule copie de l'identificateur de threads windows.  Si le thread Win32 se termine, cet identificateur est pas assigné et peut ensuite être assigné à un autre thread.  
  
## Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_POINTER` si un pointeur non valide a été spécifié.  
  
## Notes  
 Cette méthode peut être appelée des threads non base sans ce qui provoque une légende non base des objets hôte ou à l'interface d' [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)