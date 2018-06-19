---
title: Scriptthreadid, constantes | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADID
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADID
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc692716115ea0c205b1cfd982b189fffd54a9ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734189"
---
# <a name="scriptthreadid-constants"></a>SCRIPTTHREADID, constantes
Utilisé pour spécifier le type de thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Constantes  
  
|Constante|Valeur|Signification|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|Le thread en cours d’exécution.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|Le thread de base ; Autrement dit, le thread dans lequel le script du moteur a été instancié.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|Tous les threads.|  
  
## <a name="remarks"></a>Remarques  
 Le `SCRIPTTHREADID` type est utilisé par `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`, et `IActiveScript::InterruptScriptThread`, mais l’une des constantes peuvent uniquement être utilisées par `IActiveScript::GetScriptThreadState` et `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)