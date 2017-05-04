---
title: "BREAKREASON, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKREASON
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKREASON (énumération)"
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# BREAKREASON, &#233;num&#233;ration
Indique ce qui a provoqué l'arrêt.  
  
## Syntaxe  
  
```  
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## Membres  
  
|Membre|Description|  
|------------|-----------------|  
|BREAKREASON\_STEP|Le moteur de langage est en mode de progression.|  
|BREAKREASON\_BREAKPOINT|Le moteur de langue a rencontré un point d'arrêt explicite.|  
|BREAKREASON\_DEBUGGER\_BLOCK|Le moteur de langue a rencontré un bloc de débogueur sur un autre thread.|  
|BREAKREASON\_HOST\_INITIATED|L'hôte a demandé un saut de ligne.|  
|BREAKREASON\_LANGUAGE\_INITIATED|Le moteur de langue a demandé un saut de ligne.|  
|BREAKREASON\_DEBUGGER\_HALT|Le débogueur IDE a demandé un saut de ligne.|  
|BREAKREASON\_ERROR|Une erreur d'exécution a provoqué l'arrêt.|  
|BREAKREASON\_JIT|Provoqué par le démarrage de débogage JIT.|  
  
## Voir aussi  
 [Débogueur de script actif, constantes, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)