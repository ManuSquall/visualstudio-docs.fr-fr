---
title: "IActiveScript::GetScriptThreadState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptThreadState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptThreadState"
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::GetScriptThreadState
Récupère l'état actuel d'un thread de script.  
  
## Syntaxe  
  
```  
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### Paramètres  
 `stidThread`  
 \[in\]  Identificateur du thread dont l'état est approprié, ou l'un des identificateurs spéciaux suivants de thread :  
  
|Valeur|Signification|  
|------------|-------------------|  
|SCRIPTTHREADID\_BASE|Le thread de base ; autrement dit, le thread dans lequel le moteur de script a été instancié.|  
|SCRIPTTHREADID\_CURRENT|Le thread en cours.|  
  
 `pstsState`  
 \[out\]  Adresse d'une variable qui accepte l'état du thread indiqué.  L'état est indiqué par une des valeurs de constantes nommées définies par l'énumération de [SCRIPTTHREADSTATE, énumération](../../winscript/reference/scriptthreadstate-enumeration.md) .  Si ce paramètre ne reconnaît pas le thread actuel, l'état peut changer à tout moment.  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|Succès.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L'appel à n'a pas été conçu \(par exemple, le moteur de script n'a pas encore été chargé ou n'a pas été initialisé.\)|  
  
## Notes  
 Cette méthode peut être appelée des threads non base sans ce qui provoque une légende non base des objets hôte ou à l'interface d' [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)