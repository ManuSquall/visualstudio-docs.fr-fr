---
title: Énumération BREAKRESUMEACTION | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: d2db56b66a544a31df3ac3a622568ecd29a33d12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572605"
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