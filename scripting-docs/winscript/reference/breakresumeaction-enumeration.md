---
title: "BREAKRESUMEACTION, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKRESUMEACTION (énumération)"
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# BREAKRESUMEACTION, &#233;num&#233;ration
Décrit les différentes façons de poursuivre à partir d'un point d'arrêt.  
  
## Syntaxe  
  
```  
typedef enum tagBREAKRESUME_ACTION {    BREAKRESUMEACTION_ABORT,    BREAKRESUMEACTION_CONTINUE,    BREAKRESUMEACTION_STEP_INTO,    BREAKRESUMEACTION_STEP_OVER,    BREAKRESUMEACTION_STEP_OUT,    BREAKRESUMEACTION_IGNORE,    BREAKRESUMEACTION_STEP_DOCUMENT, } BREAKRESUMEACTION;  
```  
  
## Membres  
  
|Membre|Description|  
|------------|-----------------|  
|BREAKRESUMEACTION\_ABORT|Interrompt l'application.|  
|BREAKRESUMEACTION\_CONTINUE|Poursuit l'exécution.|  
|BREAKRESUMEACTION\_STEP\_INTO|Effectue un pas à pas détaillé dans une procédure.|  
|BREAKRESUMEACTION\_STEP\_OVER|Effectue un pas à pas principal dans une procédure.|  
|BREAKRESUMEACTION\_STEP\_OUT|Sort de la procédure en cours.|  
|BREAKRESUMEACTION\_IGNORE|Poursuit l'exécution avec l'état.|  
|BREAKRESUMEACTION\_STEP\_DOCUMENT|Passe au document suivant.|  
  
## Voir aussi  
 [Débogueur de script actif, constantes, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)