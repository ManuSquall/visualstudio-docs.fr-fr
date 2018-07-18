---
title: Scriptthreadstate, énumération | Documents Microsoft
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
ms.openlocfilehash: 9e18cc6f5f2afb1dcea6835983f69f6a6f7b9280
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733919"
---
# <a name="scriptthreadstate-enumeration"></a>SCRIPTTHREADSTATE, énumération
Spécifie l’état d’un thread dans un moteur de script. Cette énumération est utilisée par le [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>Valeurs d’énumération  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|Thread spécifié n’est pas actuellement un événement sous forme de script, le texte de script de traitement exécuté immédiatement, de maintenance ou une macro de script en cours d’exécution.|  
|SCRIPTTHREADSTATE_RUNNING|Thread spécifié est activement à traiter un événement sous forme de script, le texte de script de traitement exécuté immédiatement, ou une macro de script en cours d’exécution.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de script actives, énumérations et codes d’erreur](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)