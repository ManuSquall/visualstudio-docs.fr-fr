---
title: Énumération BREAKREASON | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKREASON
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f656bdf4e3bc85a014ff8d3011708799aa44bcd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572618"
---
# <a name="breakreason-enumeration"></a>Énumération BREAKREASON
Indique ce qui a provoqué l'arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|BREAKREASON_STEP|Le moteur de langage est en mode pas à pas.|  
|BREAKREASON_BREAKPOINT|Le moteur de langage a rencontré un point d’arrêt explicite.|  
|BREAKREASON_DEBUGGER_BLOCK|Le moteur de langage a rencontré un bloc de débogueur sur un autre thread.|  
|BREAKREASON_HOST_INITIATED|L’hôte a demandé une interruption.|  
|BREAKREASON_LANGUAGE_INITIATED|Le moteur de langage a demandé une interruption.|  
|BREAKREASON_DEBUGGER_HALT|L’IDE du débogueur a demandé un arrêt.|  
|BREAKREASON_ERROR|Une erreur d’exécution est à l’origine de l’arrêt.|  
|BREAKREASON_JIT|Provoqué par le démarrage du débogage juste-à-temps.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)