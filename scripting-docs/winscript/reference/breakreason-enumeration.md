---
title: Énumération BREAKREASON | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: bf1baa8b627df50db33cbd86302ce06e80c1cf34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641019"
---
# <a name="breakreason-enumeration"></a>Énumération BREAKREASON
Indique ce qui a provoqué l'arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|BREAKREASON_STEP|Le moteur de langage est en mode pas à pas.|  
|BREAKREASON_BREAKPOINT|Le moteur de langage a rencontré un point d’arrêt explicite.|  
|BREAKREASON_DEBUGGER_BLOCK|Le moteur de langage a détecté un bloc de débogueur sur un autre thread.|  
|BREAKREASON_HOST_INITIATED|L’hôte demandé une pause.|  
|BREAKREASON_LANGUAGE_INITIATED|Le moteur de langage a demandé une pause.|  
|BREAKREASON_DEBUGGER_HALT|Le débogueur IDE demandé une pause.|  
|BREAKREASON_ERROR|Une erreur d’exécution a provoqué l’arrêt.|  
|BREAKREASON_JIT|Dû au démarrage du débogage JIT.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)