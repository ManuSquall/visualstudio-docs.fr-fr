---
title: IActiveScript::GetScriptThreadState | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetScriptThreadState
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b11b8566857bc70aaeac5bdf8e8e357fa5d9c2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Récupère l’état actuel d’un thread de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `stidThread`  
 [in] Identificateur du thread dont l’état est souhaité, ou un des identificateurs de thread spéciaux suivants :  
  
|Valeur|Signification|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Le thread de base ; Autrement dit, le thread dans lequel le script du moteur a été instancié.|  
|SCRIPTTHREADID_CURRENT|Le thread en cours d’exécution.|  
  
 `pstsState`  
 [out] Adresse d’une variable qui reçoit l’état du thread indiqué. L’état est indiqué par une des valeurs constantes nommées définies par le [scriptthreadstate, énumération](../../winscript/reference/scriptthreadstate-enumeration.md) énumération. Si ce paramètre n’identifie pas le thread en cours, l’état peut changer à tout moment.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n'a pas encore été chargé ou initialisé).|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode peut être appelée à partir de threads de l’autre base sans résultant dans une légende de l’autre base d’héberger des objets ou à la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)