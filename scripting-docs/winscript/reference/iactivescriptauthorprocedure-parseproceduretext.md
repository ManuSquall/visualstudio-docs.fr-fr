---
title: "IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthorProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthorProcedure::ParseProcedureText"
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthorProcedure::ParseProcedureText
Analyse une procédure de code, ajoute le texte de la procédure de code au moteur de création de script, et crée un objet d' `IScriptEntry` qui correspond à la procédure de code.  
  
## Syntaxe  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### Paramètres  
 `pszCode`  
 \[in\]  le texte de script à analyser.  
  
 `pszFormalParams`  
 \[in\]  L'adresse des noms de paramètre formel de la procédure.  Les noms de paramètres doivent être séparés par des séparateurs appropriés pour le moteur de création de script.  Les noms ne doivent pas être insérés dans les parenthèses.  
  
 `pszProcedureName`  
 \[in\]  l'adresse du nom de procédure à analyser.  
  
 `pszItemName`  
 \[in\]  L'adresse de mémoire tampon qui contient le nom d'élément associé à l'objet d' `IScriptEntry` .  
  
 `pszDelimiter`  
 \[in\]  l'adresse du séparateur d'END\-de\-script\-bloc.  Lorsque `pszCode` est analysé d'un flux de texte, l'hôte utilise généralement un séparateur \(par exemple deux guillemets simples\), pour détecter la fin du bloc de script.  Définissez ce paramètre POUR ANNULER s'il n'existe aucun séparateur pour marquer la fin du bloc de script.  
  
 `dwCookie`  
 \[in\]  Une valeur définie par l'application associée au nouvel objet d' `IScriptEntry` .  
  
 `dwFlags`  
 \[in\] Non utilisé.  
  
 `pdispFor`  
 \[in\] Non utilisé.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Le moteur actuelle d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] n'applique pas cette méthode.  
  
## Voir aussi  
 [IActiveScriptAuthorProcedure, interface](../../winscript/reference/iactivescriptauthorprocedure-interface.md)