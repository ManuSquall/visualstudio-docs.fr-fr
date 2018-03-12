---
title: IActiveScript::GetCurrentScriptThreadID | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.GetCurrentScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5921dc4d0f9a9bf0d505fece0f47354cb16d440c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Récupère un identificateur de script-moteur-définies pour le thread en cours d’exécution. L’identificateur peut être utilisé dans les appels suivants aux méthodes de contrôle de l’exécution de thread de script telles que le [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstidThread`  
 [out] Adresse d’une variable qui reçoit l’identificateur du thread de script associé au thread actuel. L’interprétation de cet identificateur est le moteur de script, mais il peut être une copie de l’identificateur de thread Windows. Si le thread Win32 se termine, cet identificateur devient non attribué et peut ensuite être attribué à un autre thread.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_POINTER` si un pointeur non valide a été spécifié.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode peut être appelée à partir de threads de l’autre base sans résultant dans une légende de l’autre base d’héberger des objets ou à la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)