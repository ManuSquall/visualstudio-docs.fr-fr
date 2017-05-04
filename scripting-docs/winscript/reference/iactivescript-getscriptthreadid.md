---
title: "IActiveScript::GetScriptThreadID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptThreadID"
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::GetScriptThreadID
Récupère un identificateur script\-engine\- défini pour le thread associé au thread donné Win32.  
  
## Syntaxe  
  
```  
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### Paramètres  
 `dwWin32ThreadID` ,  
 \[in\]  Identificateur du thread d'un thread en cours de exécution Win32 dans le processus actuel.  Utilisez la fonction d' [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) pour récupérer l'identificateur du thread du thread en cours.  
  
 `pstidThread` ,  
 \[out\]  Adresse d'une variable qui accepte l'identificateur du thread de script associé au thread donné Win32.  La traduction de cet identificateur est laissée au moteur de script, mais elle peut être une seule copie de l'identificateur de threads windows.  Notez que si le thread Win32 se termine, cet identificateur est pas assigné et peut ensuite être assigné à un autre thread.  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|Succès.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L'appel à n'a pas été conçu \(par exemple, le moteur de script n'a pas encore été chargé ou n'a pas été initialisé\) et n'a pas été échoué par conséquent.|  
  
## Notes  
 L'identificateur extrait peut être utilisé dans les appels suivants à des méthodes de contrôle d'exécution de thread de script telles que la méthode d' [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
 Cette méthode peut être appelée des threads non base sans ce qui provoque une légende non base des objets hôte ou à l'interface d' [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
## Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)