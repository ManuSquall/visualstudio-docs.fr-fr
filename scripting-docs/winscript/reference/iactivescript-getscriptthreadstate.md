---
title: IActiveScript::GetScriptThreadState | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b191f1b70aa522cba0a04e0781ada69a8fe5ca5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097524"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Récupère l’état actuel d’un thread de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `stidThread`  
 [in] Identificateur du thread pour lequel l’état est souhaitée, ou un des identificateurs de thread spéciaux suivants :  
  
|Value|Signification|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Le thread de base ; Autrement dit, le thread dans lequel le script du moteur a été instancié.|  
|SCRIPTTHREADID_CURRENT|Le thread en cours d’exécution.|  
  
 `pstsState`  
 [out] Adresse d’une variable qui reçoit l’état du thread indiqué. L’état est indiqué par une des valeurs de constantes nommées définies par le [scriptthreadstate, énumération](../../winscript/reference/scriptthreadstate-enumeration.md) énumération. Si ce paramètre n’identifie pas le thread actuel, l’état peut changer à tout moment.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n'a pas encore été chargé ou initialisé).|  
  
## <a name="remarks"></a>Notes  
 Cette méthode peut être appelée à partir de threads de base autre sans résultant dans une légende de base autre à des objets de l’hôte ou à la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)