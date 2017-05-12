---
title: "IActiveScriptAuthor::RemoveTypeLib | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.RemoveTypeLib
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::RemoveTypeLib"
ms.assetid: 232c3698-024d-4549-8fbc-cb0d3ac17dc5
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptAuthor::RemoveTypeLib
Supprime une bibliothèque de types de l'espace de noms du moteur de création de script.  
  
## Syntaxe  
  
```  
HRESULT RemoveTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor  
);  
```  
  
#### Paramètres  
 `rguidTypeLib`  
 \[in\]  Le CLSID \(identificateur de classe\) de la bibliothèque de types à supprimer.  
  
 `dwMajor`  
 \[in\]  Le numéro de version principale.  
  
 `dwMinor`  
 \[in\]  le numéro de version secondaire.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IActiveScriptAuthor, interface](../../winscript/reference/iactivescriptauthor-interface.md)