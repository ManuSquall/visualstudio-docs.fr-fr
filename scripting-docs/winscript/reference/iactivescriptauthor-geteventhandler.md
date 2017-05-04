---
title: "IActiveScriptAuthor::GetEventHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetEventHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetEventHandler"
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptAuthor::GetEventHandler
Retourne le scriptlet qui a les attributs spécifiés.  
  
## Syntaxe  
  
```  
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### Paramètres  
 `pdisp`  
 \[in\]  L'objet d' `IDispatch` qui correspond à `NamedItem` auquel le scriptlet est attaché.  
  
 `pszItem`  
 \[in\]  L'adresse de mémoire tampon de l'identificateur de niveau supérieur du nom qualifié complet de scriptlet dans l'hôte.  
  
 `pszSubItem`  
 \[in\]  L'adresse de mémoire tampon de l'identificateur de second niveau de nom qualifié complet de scriptlet dans l'hôte.  Définissez POUR ANNULER si le nom a un seul niveau.  
  
 `pszEvent`  
 \[in\]  L'adresse d'une mémoire tampon qui contient le nom de l'événement.  Le scriptlet est un gestionnaire d'événements pour cet événement.  
  
 `ppse`  
 \[out\]  L'adresse d'une variable qui reçoit un pointeur vers l'interface d' `IScriptEntry` du scriptlet qui a les attributs spécifiés.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IActiveScriptAuthor, interface](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry, interface](../../winscript/reference/iscriptentry-interface.md)