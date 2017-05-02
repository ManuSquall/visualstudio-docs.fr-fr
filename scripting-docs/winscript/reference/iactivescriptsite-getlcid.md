---
title: "IActiveScriptSite::GetLCID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetLCID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetLCID"
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetLCID
Récupère l'identificateur de paramètres régionaux associé à l'interface utilisateur de l'hôte.  Le moteur de script utilise l'identificateur pour garantir que l'erreur chaînes et d'autres éléments d'interface utilisateur générés par le moteur semblez dans la langue appropriée.  
  
## Syntaxe  
  
```  
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### Paramètres  
 `plcid`  
 \[out\]  L'adresse d'une variable qui accepte l'identificateur de paramètres régionaux pour les éléments de l'interface utilisateur affichée par le moteur de script.  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|Succès.|  
|`E_NOTIMPL`|Cette méthode n'est pas implémentée.  Utilisez les paramètres régionaux définis par le système.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
  
## Notes  
 Si cette méthode retourne `E_NOTIMPL`, l'identificateur de paramètres régionaux défini par le système doit être utilisé.  
  
## Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)