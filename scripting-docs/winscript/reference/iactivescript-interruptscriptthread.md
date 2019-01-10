---
title: IActiveScript::InterruptScriptThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.InterruptScriptThread
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d20847245e25ec6227bb043df3190a6db5f095d5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088931"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Interrompt l’exécution d’un thread en cours d’exécution de script (un récepteur d’événements, une exécution immédiate ou un appel de macro). Cette méthode peut être utilisée pour mettre fin à un script qui est bloqué (par exemple, dans une boucle infinie). Elle peut être appelée à partir de threads de base autre sans résultant dans une légende de base autre à des objets de l’hôte ou à la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `stidThread`  
 [in] Identificateur du thread à interruption ou à des valeurs d’identificateur de thread spéciales suivantes :  
  
|Value|Signification|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Tous les threads. L’interruption est appliquée à toutes les méthodes de script en cours. Notez que, sauf si l’appelant a demandé que le script déconnectés, l’événement de script suivant, le code de script à exécuter à nouveau en appelant le [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) méthode avec le SCRIPTSTATE_DISCONNECTED ou L’indicateur SCRIPTSTATE_INITIALIZED défini.|  
|SCRIPTTHREADID_BASE|Le thread de base ; Autrement dit, le thread dans lequel le script du moteur a été instancié.|  
|SCRIPTTHREADID_CURRENT|Le thread en cours d’exécution.|  
  
 `pexcepinfo`  
 [in] Adresse d’un `EXCEPINFO` structure contenant les informations d’erreur qui doivent être signalées au script abandonné.  
  
 `dwFlags`  
 [in] Indicateurs d’option associés à l’interruption. Peut avoir l'une des valeurs suivantes :  
  
|Value|Signification|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Si la prise en charge, entrez le débogueur du moteur de script au point de l’exécution de script actuel.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Si la prise en charge par le langage de script du moteur, laisser le script de gérer l’exception. Sinon, la méthode de script est abandonnée et le code d’erreur est retourné à l’appelant ; Autrement dit, l’événement source ou la macro demandeur.|  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n'a pas encore été chargé ou initialisé).|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)