---
title: "IActiveScriptAuthor::ParseScriptText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.ParseScriptText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::ParseScriptText"
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor::ParseScriptText
Analyse le texte de script, ajoute du texte au moteur de création de script, et crée un objet d' `IScriptEntry` qui correspond au bloc de script.  
  
## Syntaxe  
  
```  
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### Paramètres  
 `pszCode`  
 \[in\]  le texte de script à analyser.  
  
 `pszItemName`  
 \[in\]  L'adresse de mémoire tampon qui contient le nom de l'élément associé avec le bloc de script.  
  
 `pszDelimiter`  
 \[in\]  l'adresse du séparateur d'END\-de\-script\-bloc.  Lorsque `pszCode` est analysé d'un flux de texte, l'hôte utilise généralement un séparateur \(par exemple deux guillemets simples\), pour détecter la fin du bloc de script.  Définissez ce paramètre POUR ANNULER s'il n'existe aucun séparateur pour identifier la fin du bloc de script.  
  
 `dwCookie`  
 \[in\]  Une valeur définie par l'application associée au nouvel objet d' `IScriptEntry` .  
  
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