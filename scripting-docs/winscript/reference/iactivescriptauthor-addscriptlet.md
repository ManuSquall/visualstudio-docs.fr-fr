---
title: "IActiveScriptAuthor::AddScriptlet | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddScriptlet"
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptAuthor::AddScriptlet
Ajoute un scriptlet de code comme un enfant de l'objet d' `IScriptNode` de niveau racine.  Dans l'hôte, est autorisé à le nom qualifié complet du scriptlet d'avoir deux niveaux.  
  
## Syntaxe  
  
```  
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### Paramètres  
 `pszDefaultName`  
 \[in\]  L'adresse du nom par défaut à associer au scriptlet.  
  
 `pszCode`  
 \[in\]  l'adresse du texte de scriptlet.  
  
 `pszItemName`  
 \[in\]  L'adresse de mémoire tampon de l'identificateur de niveau supérieur du nom qualifié complet de scriptlet dans l'hôte.  
  
 `pszSubItemName`  
 \[in\]  L'adresse de mémoire tampon de l'identificateur de second niveau de nom qualifié complet de scriptlet dans l'hôte.  Définissez POUR ANNULER si le nom a un seul niveau.  
  
 `pszEventName`  
 \[in\]  L'adresse d'une mémoire tampon qui contient le nom de l'événement pour lequel le scriptlet est un gestionnaire d'événements.  
  
 `pszDelimiter`  
 \[in\]  l'adresse du séparateur d'END\-de\-script\-bloc.  Lorsque `pszCode` est analysé d'un flux de texte, l'hôte utilise généralement un séparateur \(par exemple deux guillemets simples\), pour détecter la fin du bloc de script.  Définissez ce paramètre POUR ANNULER si un séparateur ne marque pas la fin du bloc de script.  
  
 `dwCookie`  
 \[in\]  une valeur définie par l'application qui est utilisée pour associer le scriptlet avec un objet hôte.  
  
 `dwFlags`  
 \[in\] Non utilisé.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IActiveScriptAuthor, interface](../../winscript/reference/iactivescriptauthor-interface.md)