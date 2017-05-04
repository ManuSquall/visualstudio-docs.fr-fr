---
title: "SCRIPTSTATE, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTSTATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTSTATE (enum)"
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# SCRIPTSTATE, &#233;num&#233;ration
Spécifie l'état d'un moteur de script.  Cette énumération est utilisée par les méthodes d' [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , d' [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) , et d' [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .  
  
## Syntaxe  
  
```  
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## Valeurs d'énumération  
  
|||  
|-|-|  
|SCRIPTSTATE\_UNINITIALIZED|Le script vient d'être créé, mais pas encore initialisé à l'aide d'une interface et [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) d' `IPersist*` .|  
|SCRIPTSTATE\_INITIALIZED|Le script a été initialisé, mais n'exécute pas \(la connexion à d'autres objets ou événements de descendant\) ou n'exécute pas de code.  Le code peut être interrogé pour l'exécution en appelant la méthode d' [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md) .|  
|SCRIPTSTATE\_STARTED|Le script peut exécuter du code, mais ne descend pas encore les événements des objets ajoutés par la méthode d' [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|SCRIPTSTATE\_CONNECTED|Le script est chargé et connecté pour les événements de descendant.|  
|SCRIPTSTATE\_DISCONNECTED|Script est chargé et a un état à l'exécution de l'exécution, mais est temporairement déconnecté des événements de descendant.|  
|SCRIPTSTATE\_CLOSED|Le script a été fermé.  Le moteur de script plus fonctionne et ne retourne des erreurs pour la plupart des méthodes.|  
  
## Voir aussi  
 [Script actif, constantes, énumérations et codes d'erreur](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)