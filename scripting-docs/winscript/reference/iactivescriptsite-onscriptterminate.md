---
title: "IActiveScriptSite::OnScriptTerminate | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnScriptTerminate
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnScriptTerminate"
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnScriptTerminate
Signale à l'hôte que le script est terminé l'exécution.  
  
## Syntaxe  
  
```  
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### Paramètres  
 `pvarResult`  
 \[in\]  Adresse d'une variable contenant le résultat de script, ou `NULL` si le script ne produit aucun résultat.  
  
 `pexcepinfo`  
 \[in\]  L'adresse d'une structure d' `EXCEPINFO` qui contient des informations sur les exceptions a généré lorsque le script est terminé, ou `NULL` si aucune exception n'est générée.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  
  
## Notes  
 Le moteur de script appelle cette méthode avant l'appel à la méthode d' [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) , avec l'indicateur de SCRIPTSTATE\_INITIALIZED, soit terminé.  Cette méthode peut être utilisée pour retourner l'état et les résultats d'achèvement à l'hôte.  Notez que de nombreux langages de script, qui sont basés sur des événements de descendant de l'hôte, ont des durées définies par l'hôte.  Dans ce cas, cette méthode ne peut jamais être appelée.  
  
## Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)