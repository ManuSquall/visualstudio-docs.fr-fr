---
title: "SCRIPTTHREADSTATE, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTTHREADSTATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTTHREADSTATE (enum)"
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# SCRIPTTHREADSTATE, &#233;num&#233;ration
Spécifie l'état d'un thread dans un moteur de script.  Cette énumération est utilisée par la méthode [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md).  
  
## Syntaxe  
  
```  
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## Valeurs d'énumération  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE\_NOTINSCRIPT|Le thread spécifié en cours ne services pas un script événement, traite le texte immédiatement l'exécution du script, ou n'exécute pas une macro de script.|  
|SCRIPTTHREADSTATE\_RUNNING|Le thread spécifié activement services un script événement, traite le texte immédiatement l'exécution du script, ou exécute une macro de script.|  
  
## Voir aussi  
 [Script actif, constantes, énumérations et codes d'erreur](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)