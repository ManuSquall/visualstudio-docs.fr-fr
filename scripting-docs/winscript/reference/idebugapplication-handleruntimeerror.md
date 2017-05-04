---
title: "IDebugApplication::HandleRuntimeError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.HandleRuntimeError
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::HandleRuntimeError"
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::HandleRuntimeError
Entraîne le blocage du thread actuel et envoie une notification de l'erreur au débogueur IDE.  
  
## Syntaxe  
  
```  
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### Paramètres  
 `pErrorDebug`  
 \[in\]  l'erreur qui s'est produite.  
  
 `pScriptSite`  
 \[in\]  Le site de script du thread.  
  
 `pbra`  
 \[out\]  Action à effectuer lorsque le débogueur continue l'application.  
  
 `perra`  
 \[out\]  Action à effectuer lorsque le débogueur continue l'application en cas de erreur.  
  
 `pfCallOnScriptError`  
 \[out\]  Balise qui est `TRUE` si le moteur appelle la méthode d' `IActiveScriptSite::OnScriptError` .  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Un moteur de langage appelle cette méthode dans le contexte d'un thread qui provoque une erreur d'exécution.  Cette méthode entraîne le blocage du thread actuel et envoie une notification d'erreur à envoyer au débogueur IDE.  Lorsque le débogueur IDE reprend l'application, les cette méthode retourne à l'action à effectuer.  
  
> [!NOTE]
>  Alors que dans le défaut à l'exécution, le moteur de langage peut être appelé par le thread pour effectuer des tâches telles que les énumèrent les frames de pile ou évalue des expressions.  
  
## Voir aussi  
 [IDebugApplication, interface](../../winscript/reference/idebugapplication-interface.md)   
 [IActiveScriptErrorDebug, interface](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [BREAKRESUMEACTION, énumération](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION, énumération](../../winscript/reference/errorresumeaction-enumeration.md)