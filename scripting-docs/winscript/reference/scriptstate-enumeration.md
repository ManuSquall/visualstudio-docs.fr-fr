---
title: Énumération SCRIPTSTATE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 10dd6366e2d0783ec2e9d6bdadc001e9f999901e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575685"
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE, énumération
Spécifie l’état d’un moteur de script. Cette énumération est utilisée par les méthodes [IActiveScript :: GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript :: SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) et [IActiveScriptSite :: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .  
  
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
|SCRIPTSTATE_UNINITIALIZED|Le script vient d’être créé, mais n’a pas encore été initialisé à l’aide d’une interface `IPersist*` et [IActiveScript :: SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|Le script a été initialisé, mais n’est pas en cours d’exécution (connexion à d’autres objets ou réception d’événements) ou exécution de code. Le code peut être interrogé pour exécution en appelant la méthode [IActiveScriptParse ::P arsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md) .|  
|SCRIPTSTATE_STARTED|Le script peut exécuter du code, mais ne reçoit pas encore les événements des objets ajoutés par la méthode [IActiveScript :: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|SCRIPTSTATE_CONNECTED|Le script est chargé et connecté pour la réception des événements.|  
|SCRIPTSTATE_DISCONNECTED|Le script est chargé et a un état d’exécution au moment de l’exécution, mais il est temporairement déconnecté de la réception des événements.|  
|SCRIPTSTATE_CLOSED|Le script a été fermé. Le moteur de script ne fonctionne plus et retourne des erreurs pour la plupart des méthodes.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de script actives, énumérations et codes d’erreur](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)