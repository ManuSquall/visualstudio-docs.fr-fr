---
title: "BREAKPOINT_STATE, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKPOINT_STATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKPOINT_STATE (énumération)"
ms.assetid: 7adc9341-129a-4948-9669-0906d545fd5c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# BREAKPOINT_STATE, &#233;num&#233;ration
Indique l'état d'un point d'arrêt.  
  
## Syntaxe  
  
```  
typedef enum tagBREAKPOINT_STATE {  
   BREAKPOINT_DELETED = 0,  
   BREAKPOINT_DISABLED = 1,  
   BREAKPOINT_ENABLED = 2  
} BREAKPOINT_STATE;  
```  
  
## Membres  
  
|Membre|Description|  
|------------|-----------------|  
|BREAKPOINT\_DELETED|Le point d'arrêt n'existe plus, mais il reste des références à celui\-ci.|  
|BREAKPOINT\_DISABLED|Le point d'arrêt existe mais est désactivé.|  
|BREAKPOINT\_ENABLED|Le point d'arrêt existe et est activé.|  
  
## Voir aussi  
 [Débogueur de script actif, constantes, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)