---
title: "IActiveScriptSite::GetDocVersionString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetDocVersionString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetDocVersionString"
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetDocVersionString
Extrait une chaîne hôte définie qui identifie la version du document actif.  Si le document associé a changé en dehors de Windows Script \(comme dans le cas d'une page HTML est modifiée avec le bloc\-notes\), le moteur de script peut enregistrer faire avec son état persistant, forçant une recompilation la prochaine fois que le script est chargé.  
  
## Syntaxe  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### Paramètres  
 `pstrVersionString`  
 \[out\]  Adresse de la chaîne définie hôte de document.  
  
## Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_NOTIMPL` si cette méthode n'est pas prise en charge.  
  
## Notes  
 Si `E_NOTIMPL` est retourné, le moteur de script doit supposer que le script est synchronisé avec le du document.  
  
## Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)