---
title: "IRemoteDebugApplication::ResumeFromBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.ResumeFromBreakPoint
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::ResumeFromBreakPoint"
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::ResumeFromBreakPoint
Continue une application qui est actuellement dans un point d'arrêt.  
  
## Syntaxe  
  
```  
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### Paramètres  
 `prptFocus`  
 \[in\]  Pour les modes de progression, le thread qui doit être affecté par le mode de progression.  
  
 `bra`  
 \[in\]  L'action à effectuer en reprenant l'application.  
  
 `era`  
 \[in\]  L'action de rentrer le cas que l'application a été arrêté en raison d'une erreur.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode continue une application qui est actuellement dans un point d'arrêt.  
  
## Voir aussi  
 [IRemoteDebugApplication, interface](../../winscript/reference/iremotedebugapplication-interface.md)   
 [BREAKRESUMEACTION, énumération](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION, énumération](../../winscript/reference/errorresumeaction-enumeration.md)