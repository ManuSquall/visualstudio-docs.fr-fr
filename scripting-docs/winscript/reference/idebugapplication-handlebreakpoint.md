---
title: "IDebugApplication::HandleBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.HandleBreakPoint
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::HandleBreakPoint"
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::HandleBreakPoint
Entraîne le blocage du thread actuel et envoie une notification du point d'arrêt au débogueur IDE.  
  
## Syntaxe  
  
```  
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### Paramètres  
 `br`  
 \[in\]  La raison de l'arrêt.  
  
 `pbra`  
 \[out\]  Action à effectuer lorsque le débogueur continue l'application.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Un moteur de langage appelle cette méthode dans le contexte d'un thread qui atteigne un point d'arrêt.  Cette méthode bloque le thread actuel et envoie une notification de point d'arrêt au débogueur IDE.  Lorsque le débogueur continue l'application, le paramètre d' `pbra` spécifie l'action à effectuer.  
  
> [!NOTE]
>  Le moteur de langage peut être appelé par le thread pour effectuer des tâches telles énumèrent les frames de pile ou évaluer des expressions pendant le point d'arrêt.  
  
 Cette méthode provoque `IApplicationDebugger::onHandleBreakPoint` d'être appelé.  
  
## Voir aussi  
 [IDebugApplication, interface](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [BREAKREASON, énumération](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION, énumération](../../winscript/reference/breakresumeaction-enumeration.md)