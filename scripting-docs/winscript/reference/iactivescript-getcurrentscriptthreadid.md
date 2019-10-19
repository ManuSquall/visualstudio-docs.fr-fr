---
title: 'IActiveScript :: GetCurrentScriptThreadID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetCurrentScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dedb16e0c007ed05370fb54835f84f00784c1ae4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575766"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Récupère un identificateur défini par le moteur de script pour le thread en cours d’exécution. L’identificateur peut être utilisé dans les appels ultérieurs aux méthodes de contrôle d’exécution de thread de script telles que la méthode [IActiveScript :: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstidThread`  
 à Adresse d’une variable qui reçoit l’identificateur de thread de script associé au thread actuel. L’interprétation de cet identificateur est laissée au moteur de script, mais il peut s’agir simplement d’une copie de l’identificateur de thread Windows. Si le thread Win32 s’arrête, cet identificateur devient non assigné et peut ensuite être assigné à un autre thread.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_POINTER` si un pointeur non valide a été spécifié.  
  
## <a name="remarks"></a>Notes  
 Cette méthode peut être appelée à partir de threads non de base sans aboutir à un appel de non-base pour héberger des objets ou à l’interface [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)