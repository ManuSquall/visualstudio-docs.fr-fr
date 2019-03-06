---
title: Scriptthreadstate, énumération | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2c66d078effd510b3f64cf1f443926984ff2e282
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347669"
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