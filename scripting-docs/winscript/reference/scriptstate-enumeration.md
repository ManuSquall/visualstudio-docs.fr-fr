---
title: Énumération SCRIPTSTATE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff935e54e42eef6691948a7e0d91a495c5153adc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097797"
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE, énumération
Spécifie l’état d’un moteur de script. Cette énumération est utilisée par le [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) , et [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) méthodes.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## <a name="enumeration-values"></a>Valeurs d’énumération  
  
|||  
|-|-|  
|SCRIPTSTATE_UNINITIALIZED|Script vient d’être créé, mais le n'a pas encore été initialisé à l’aide un `IPersist*` interface et [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|Script a été initialisé, mais n'est pas en cours d’exécution (se connecter aux autres objets ou la réception des événements) ou l’exécution de n’importe quel code. Code peut être interrogé pour l’exécution en appelant le [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md) (méthode).|  
|SCRIPTSTATE_STARTED|Script peut exécuter du code, mais n’est ne pas encore recevoir les événements d’objets ajoutés par le [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) (méthode).|  
|SCRIPTSTATE_CONNECTED|Script est chargé et connecté pour la réception des événements.|  
|SCRIPTSTATE_DISCONNECTED|Script est chargé et a un état d’exécution, mais n’est temporairement déconnecté de la réception des événements.|  
|SCRIPTSTATE_CLOSED|Script a été fermé. Le moteur de script ne fonctionne plus et retourne des erreurs pour la plupart des méthodes.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de script actives, énumérations et codes d’erreur](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)