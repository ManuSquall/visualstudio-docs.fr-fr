---
title: "Appbreakflags, énumération | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: APPBREAKFLAGS
apilocation: scrobj.dll
helpviewer_keywords: APPBREAKFLAGS constants
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 126dcd704a60b591b71913f2e8e739de35c14636
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="appbreakflags-enumeration"></a>APPBREAKFLAGS, énumération
Indique l'état actuel du débogage des applications et des threads.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_APPBREAKFLAGS{APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,APPBREAKFLAG_STEP= 0x00010000,APPBREAKFLAG_NESTED= 0x00020000,APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,APPBREAKFLAG_IN_BREAKPOINT= 0x80000000};  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Valeur|Description|  
|------------|-----------|-----------------|  
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Moteur de langage doit s’arrêter immédiatement sur tous les threads avec BREAKREASON_DEBUGGER_BLOCK.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Moteur de langage doit s’arrêter immédiatement avec BREAKREASON_DEBUGGER_HALT.|  
|APPBREAKFLAG_STEP|0x00010000|Moteur de langage doit s’arrêter immédiatement dans le thread d’exécution pas à pas avec BREAKREASON_STEP.|  
|APPBREAKFLAG_NESTED|0x00020000|L’application est en exécution imbriquée sur un point d’arrêt.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|Le débogueur à passer au niveau de la source.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0 x 00100000|Le débogueur à passer au niveau du code d’octet.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0 x 00200000|Le débogueur à passer au niveau de l’ordinateur.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Masque pour développer les types d’étape.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Un point d’arrêt est en cours.|  
  
## <a name="remarks"></a>Remarques  
 Certains indicateurs spécifient que les moteurs de langue doit être interrompu l’occasion, tandis que les autres indicateurs de spécifient le mode d’exécution pas à pas du débogueur.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogueur de Script actif, constantes, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [Énumération BREAKREASON](../../winscript/reference/breakreason-enumeration.md)