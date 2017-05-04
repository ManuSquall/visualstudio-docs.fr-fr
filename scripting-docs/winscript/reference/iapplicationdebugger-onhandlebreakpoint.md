---
title: "IApplicationDebugger::onHandleBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.onHandleBreakPoint
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::onHandleBreakPoint"
ms.assetid: 31adcecd-d6c1-4222-ab2c-32ec2fefb322
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::onHandleBreakPoint
Gère un événement de point d'arrêt.  
  
## Syntaxe  
  
```  
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### Paramètres  
 `prpt`  
 \[in\]  Le thread où le point d'arrêt s'est produit.  
  
 `br`  
 \[in\]  La raison du point d'arrêt.  
  
 `pError`  
 \[in\]  Les informations sur les erreurs d'exécution, si lorsque la valeur d' `br` est BREAKREASON\_ERROR.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode est appelée lorsqu'un point d'arrêt est atteint et `IDebugApplication::HandleBreakPoint` est appelé.  
  
 L'application reste interrompue jusqu'à ce que le débogueur appelle `IRemoteDebugApplication::ResumeFromBreakPoint`l'IDE.  
  
## Voir aussi  
 [IApplicationDebugger, interface](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)   
 [IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)   
 [BREAKREASON, énumération](../../winscript/reference/breakreason-enumeration.md)