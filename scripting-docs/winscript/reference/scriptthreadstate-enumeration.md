---
title: Scriptthreadstate, énumération | Microsoft Docs
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
ms.openlocfilehash: 906a309b25a1fe606fb37f8cbab70040e5a4c46f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840185"
---
# <a name="scriptthreadstate-enumeration"></a>SCRIPTTHREADSTATE, énumération
Spécifie l’état d’un thread dans un moteur de script. Cette énumération est utilisée par le [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) (méthode).  
  
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
|SCRIPTTHREADSTATE_NOTINSCRIPT|Thread spécifié n’est pas actuellement un événement de l’aide de scripts, texte du script de traitement exécuté immédiatement, de maintenance ou une macro de script en cours d’exécution.|  
|SCRIPTTHREADSTATE_RUNNING|Thread spécifié est activement un événement de l’aide de scripts, texte du script de traitement exécuté immédiatement, de maintenance ou une macro de script en cours d’exécution.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de script actives, énumérations et codes d’erreur](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)