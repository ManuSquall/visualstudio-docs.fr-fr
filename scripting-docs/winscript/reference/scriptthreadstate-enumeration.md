---
title: Énumération SCRIPTTHREADSTATE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc4ef840310c27ccbadce2ed4f632514b555ef98
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575652"
---
# <a name="scriptthreadstate-enumeration"></a>SCRIPTTHREADSTATE, énumération
Spécifie l’état d’un thread dans un moteur de script. Cette énumération est utilisée par la méthode [IActiveScript :: GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>Valeurs d’énumération  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|Le thread spécifié ne traite pas actuellement un événement scripté, traite immédiatement le texte du script exécuté ou exécute une macro de script.|  
|SCRIPTTHREADSTATE_RUNNING|Le thread spécifié traite activement un événement de script, en traitant le texte de script exécuté immédiatement ou en exécutant une macro de script.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de script actives, énumérations et codes d’erreur](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)