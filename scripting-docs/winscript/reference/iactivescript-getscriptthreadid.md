---
title: IActiveScript::GetScriptThreadID | Microsoft Docs
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
ms.openlocfilehash: d329e08e6a17d9edcdf26e14b468c3c56f036c00
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154398"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Récupère un identificateur de script-moteur-définies pour le thread associé au thread Win32 donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwWin32ThreadID` ,  
 [in] Identificateur du thread d’un thread Win32 en cours d’exécution dans le processus actuel. Utilisez le [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) fonction pour récupérer l’identificateur de thread du thread en cours d’exécution.  
  
 `pstidThread` ,  
 [out] Adresse d’une variable qui reçoit l’identificateur de thread de script associé au thread Win32 donné. L’interprétation de cet identificateur est laissée au moteur de script, mais il peut être uniquement une copie de l’identificateur de thread Windows. Notez que si le thread Win32 s’arrête, cet identificateur devient non attribué et peut ensuite être attribué à un autre thread.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n'a pas encore été chargé ou initialisé) et par conséquent a échoué.|  
  
## <a name="remarks"></a>Notes  
 L’identificateur récupérée peut être utilisé dans les appels suivants aux méthodes de contrôle de l’exécution de thread script tel que le [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) (méthode).  
  
 Cette méthode peut être appelée à partir de threads de base autre sans résultant dans une légende de base autre à des objets de l’hôte ou à la [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)