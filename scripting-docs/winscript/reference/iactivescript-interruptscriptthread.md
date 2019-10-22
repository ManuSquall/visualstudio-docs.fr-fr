---
title: 'IActiveScript :: InterruptScriptThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a436f973df05b945c0939f3a593640f567774277
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577265"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Interrompt l’exécution d’un thread de script en cours d’exécution (un récepteur d’événements, une exécution immédiate ou un appel de macro). Cette méthode peut être utilisée pour mettre fin à un script qui est bloqué (par exemple, dans une boucle infinie). Il peut être appelé à partir de threads non de base sans entraîner la non-exécution d’un appel de base pour héberger des objets ou la méthode [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
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
 dans Identificateur du thread à interrompre, ou l’une des valeurs d’identificateur de thread spéciales suivantes :  
  
|valeur|Signification|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Tous les threads. L’interruption est appliquée à toutes les méthodes de script actuellement en cours. Notez que, sauf si l’appelant a demandé que le script soit déconnecté, l’événement script suivant entraîne une nouvelle exécution du code de script en appelant la méthode [IActiveScript :: SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) avec l’indicateur SCRIPTSTATE_DISCONNECTED ou SCRIPTSTATE_INITIALIZED définie.|  
|SCRIPTTHREADID_BASE|Thread de base ; autrement dit, le thread dans lequel le moteur de script a été instancié.|  
|SCRIPTTHREADID_CURRENT|Thread en cours d’exécution.|  
  
 `pexcepinfo`  
 dans Adresse d’une structure `EXCEPINFO` contenant les informations d’erreur qui doivent être signalées au script abandonné.  
  
 `dwFlags`  
 dans Indicateurs d’option associés à l’interruption. Peut avoir l'une des valeurs suivantes :  
  
|valeur|Signification|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|En cas de prise en charge, entrez le débogueur du moteur de script au point d’exécution de script actuel.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|S’il est pris en charge par le langage du moteur de script, laissez le script gérer l’exception. Dans le cas contraire, la méthode de script est abandonnée et le code d’erreur est retourné à l’appelant. autrement dit, la source de l’événement ou le demandeur de macro.|  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n’a pas encore été chargé ou initialisé).|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)