---
title: IActiveScript::GetScriptThreadID | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8850319035b7b5e3a9cbbd4bbe4340e1eefacc96
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Récupère un script du moteur-identificateur défini par le thread associé au thread Win32 donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwWin32ThreadID` ,  
 [in] Identificateur du thread d’un thread Win32 en cours d’exécution dans le processus actuel. Utilisez le [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) fonction pour récupérer l’identificateur du thread du thread en cours d’exécution.  
  
 `pstidThread` ,  
 [out] Adresse d’une variable qui reçoit l’identificateur du thread de script associé au thread Win32 donné. L’interprétation de cet identificateur est le moteur de script, mais il peut être une copie de l’identificateur de thread Windows. Notez que si le thread Win32 se termine, cet identificateur devient non attribué et peut ensuite être attribué à un autre thread.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n'a pas encore été chargé ou initialisé) et par conséquent a échoué.|  
  
## <a name="remarks"></a>Remarques  
 L’identificateur récupérée peut être utilisé dans les appels suivants aux méthodes de contrôle de l’exécution de thread script tel que le [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) (méthode).  
  
 Cette méthode peut être appelée à partir de threads de l’autre base sans résultant dans une légende de l’autre base d’héberger des objets ou à la [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)