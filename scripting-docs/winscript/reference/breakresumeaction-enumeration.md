---
title: Énumération BREAKRESUMEACTION | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3186ac39353d11f327f7940ae5fc03ae2238ddd9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090466"
---
# <a name="breakresumeaction-enumeration"></a>Énumération BREAKRESUMEACTION
Décrit les différentes façons de poursuivre à partir d'un point d'arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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