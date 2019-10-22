---
title: 'IActiveScript :: GetScriptThreadID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a0fb1eebfcb6ed100056289fab6bce662f86a7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575706"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Récupère un identificateur défini par le moteur de script pour le thread associé au thread Win32 donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwWin32ThreadID` ,  
 dans Identificateur de thread d’un thread Win32 en cours d’exécution dans le processus actuel. Utilisez la fonction [IActiveScript :: GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) pour récupérer l’identificateur de thread du thread en cours d’exécution.  
  
 `pstidThread` ,  
 à Adresse d’une variable qui reçoit l’identificateur de thread de script associé au thread Win32 donné. L’interprétation de cet identificateur est laissée au moteur de script, mais il peut s’agir simplement d’une copie de l’identificateur de thread Windows. Notez que si le thread Win32 s’arrête, cet identificateur devient non assigné et peut ensuite être assigné à un autre thread.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n’a pas encore été chargé ou initialisé) et par conséquent a échoué.|  
  
## <a name="remarks"></a>Notes  
 L’identificateur récupéré peut être utilisé dans les appels ultérieurs aux méthodes de contrôle d’exécution de thread de script telles que la méthode [IActiveScript :: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
 Cette méthode peut être appelée à partir de threads non de base sans aboutir à un appel de non-base pour héberger des objets ou à l’interface [IActiveScript :: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)