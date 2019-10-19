---
title: Constantes SCRIPTTHREADID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: bf1b23b191bda29b00bf29f482332301897f9f37
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575666"
---
# <a name="scriptthreadid-constants"></a>SCRIPTTHREADID, constantes
Utilisé pour spécifier le type de thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Constantes  
  
|Constante|valeur|Signification|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|Thread en cours d’exécution.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|Thread de base ; autrement dit, le thread dans lequel le moteur de script a été instancié.|  
|SCRIPTTHREADID_ALL|Égale|Tous les threads.|  
  
## <a name="remarks"></a>Notes  
 Le type de `SCRIPTTHREADID` est utilisé par `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState` et `IActiveScript::InterruptScriptThread`, mais les constantes ne peuvent être utilisées que par `IActiveScript::GetScriptThreadState` et `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript :: GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)    
 [IActiveScript :: GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)    
 [IActiveScript :: GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)    
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)