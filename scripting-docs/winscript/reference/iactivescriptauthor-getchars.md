---
title: "IActiveScriptAuthor::GetChars | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetChars
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetChars"
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IActiveScriptAuthor::GetChars
Retourne le jeu de caractères d'achèvement d'un contexte demandé d'achèvement.  
  
## Syntaxe  
  
```  
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### Paramètres  
 `fRequestedList`  
 \[in\]  le contexte demandé d'achèvement.  
  
|Constante|Valeur|Description|  
|---------------|------------|-----------------|  
|SCRIPT\_CMPL\_ENUM\_TRIGGER|0x0001|Demande l'énumération de gauche.|  
|SCRIPT\_CMPL\_MEMBER\_TRIGGER|0x0002|Demande le contexte membre d'achèvement.|  
|SCRIPT\_CMPL\_PARAM\_TRIGGER|0x0003|Demande la liste de paramètres.|  
|SCRIPT\_CMPL\_COMMIT|0x0004|Demande la fin de la liste de paramètres.|  
  
 `pbstrChars`  
 \[out\]  les caractères qui correspondent au contexte demandé d'achèvement.  
  
|Paramètre `fRequestedList`|Caractères retournés|  
|--------------------------------|--------------------------|  
|SCRIPT\_CMPL\_ENUM\_TRIGGER|"."|  
|SCRIPT\_CMPL\_MEMBER\_TRIGGER|« \= »|  
|SCRIPT\_CMPL\_PARAM\_TRIGGER|\(« , »|  
|SCRIPT\_CMPL\_COMMIT|« \(\) »|  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IActiveScriptAuthor, interface](../../winscript/reference/iactivescriptauthor-interface.md)