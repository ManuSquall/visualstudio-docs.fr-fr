---
title: "IActiveScriptAuthor::AddTypeLib | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddTypeLib"
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptAuthor::AddTypeLib
Ajoute une bibliothèque de types dans l'espace de noms pour le script.  
  
## Syntaxe  
  
```  
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### Paramètres  
 `rguidTypeLib`  
 \[in\]  Le CLSID \(identificateur de classe\) de la bibliothèque de types à ajouter.  
  
 `dwMajor`  
 \[in\]  Le numéro de version principale.  
  
 `dwMinor`  
 \[in\]  le numéro de version secondaire.  
  
 `dwFlags`  
 \[in\] Non utilisé.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode appelle `LoadTypeLib` pour charger la bibliothèque de types.  En cas de réussite, cette méthode appelle `IActiveScriptAuthor::AddNamedItem` pour ajouter des informations de type.  
  
## Voir aussi  
 [IActiveScriptAuthor, interface](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)   
 [LoadTypeLib](http://msdn.microsoft.com/fr-fr/155b48e5-5438-409e-9342-630a6a500f60)