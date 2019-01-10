---
title: Constantes SCRIPTTHREADID | Microsoft Docs
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
ms.openlocfilehash: 27852f97cf0a78919b10043c64b1c5a7cc7d3ec5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097810"
---
# <a name="scriptthreadid-constants"></a>SCRIPTTHREADID, constantes
Permet de spécifier le type de thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Constantes  
  
|Constante|Value|Signification|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|Le thread en cours d’exécution.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|Le thread de base ; Autrement dit, le thread dans lequel le script du moteur a été instancié.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|Tous les threads.|  
  
## <a name="remarks"></a>Notes  
 Le `SCRIPTTHREADID` type est utilisé par `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`, et `IActiveScript::InterruptScriptThread`, mais l’une des constantes peuvent uniquement être utilisées par `IActiveScript::GetScriptThreadState` et `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)