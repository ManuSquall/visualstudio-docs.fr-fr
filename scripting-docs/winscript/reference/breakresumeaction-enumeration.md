---
title: "Énumération BREAKRESUMEACTION | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- BREAKRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1b830d314b1db40d7b83557d894ad6f8751bdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="breakresumeaction-enumeration"></a>Énumération BREAKRESUMEACTION
Décrit les différentes façons de poursuivre à partir d'un point d'arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum tagBREAKRESUME_ACTION {  
   BREAKRESUMEACTION_ABORT,  
   BREAKRESUMEACTION_CONTINUE,  
   BREAKRESUMEACTION_STEP_INTO,  
   BREAKRESUMEACTION_STEP_OVER,  
   BREAKRESUMEACTION_STEP_OUT,  
   BREAKRESUMEACTION_IGNORE,  
   BREAKRESUMEACTION_STEP_DOCUMENT,  
} BREAKRESUMEACTION;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|BREAKRESUMEACTION_ABORT|Interrompt l'application.|  
|BREAKRESUMEACTION_CONTINUE|Poursuit l'exécution.|  
|BREAKRESUMEACTION_STEP_INTO|Effectue un pas à pas détaillé dans une procédure.|  
|BREAKRESUMEACTION_STEP_OVER|Effectue un pas à pas principal dans une procédure.|  
|BREAKRESUMEACTION_STEP_OUT|Sort de la procédure en cours.|  
|BREAKRESUMEACTION_IGNORE|Poursuit l'exécution avec l'état.|  
|BREAKRESUMEACTION_STEP_DOCUMENT|Passe au document suivant.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)