---
title: "APPBREAKFLAGS, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: APPBREAKFLAGS
apilocation: scrobj.dll
helpviewer_keywords: 
  - "APPBREAKFLAGS (constantes)"
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# APPBREAKFLAGS, &#233;num&#233;ration
Indiquez en cours de débogage l'état des applications et des threads.  
  
## Syntaxe  
  
```cpp  
enum enum_APPBREAKFLAGS  
{  
APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,  
APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,  
APPBREAKFLAG_STEP= 0x00010000,  
APPBREAKFLAG_NESTED= 0x00020000,  
APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,  
APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,  
APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,  
APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,  
APPBREAKFLAG_IN_BREAKPOINT= 0x80000000  
};  
  
```  
  
## Membres  
  
|Membre|Valeur|Description|  
|------------|------------|-----------------|  
|APPBREAKFLAG\_DEBUGGER\_BLOCK|0x00000001|Le moteur de langage doit arrêter immédiatement sur tous les threads avec BREAKREASON\_DEBUGGER\_BLOCK.|  
|APPBREAKFLAG\_DEBUGGER\_HALT|0x00000002|Le moteur de langage doit arrêter immédiatement à BREAKREASON\_DEBUGGER\_HALT.|  
|APPBREAKFLAG\_STEP|0x00010000|Le moteur de langage doit arrêter immédiatement dans le thread de progression avec BREAKREASON\_STEP.|  
|APPBREAKFLAG\_NESTED|0x00020000|L'application est dans l'exécution imbriquée sur un point d'arrêt.|  
|APPBREAKFLAG\_STEPTYPE\_SOURCE|0x00000000|Le débogueur effectue un pas au niveau de la source.|  
|APPBREAKFLAG\_STEPTYPE\_BYTECODE|0x00100000|Le débogueur effectue un pas au niveau de code d'octets.|  
|APPBREAKFLAG\_STEPTYPE\_MACHINE|0x00200000|Le débogueur effectue un pas au niveau de l'ordinateur.|  
|APPBREAKFLAG\_STEPTYPE\_MASK|0x00F00000|Masque pour factoriser les types d'étape.|  
|APPBREAKFLAG\_IN\_BREAKPOINT|0x80000000|Un point d'arrêt est en cours.|  
  
## Notes  
 Certaines balises spécifient que les moteurs de langage doit arrêter à la prochaine possibilité, tandis que d'autres balises spécifier le mode de progression du débogueur.  
  
## Voir aussi  
 [Débogueur de script actif, constantes, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [BREAKREASON, énumération](../../winscript/reference/breakreason-enumeration.md)