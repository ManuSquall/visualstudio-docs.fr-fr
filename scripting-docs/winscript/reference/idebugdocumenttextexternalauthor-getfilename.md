---
title: "IDebugDocumentTextExternalAuthor::GetFileName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextExternalAuthor.GetFileName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentTextExternalAuthor::GetFileName"
ms.assetid: 87acdce6-acb2-4936-80dd-d624bb7dbd42
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextExternalAuthor::GetFileName
Retourne le nom de le document sans informations de chemin d'accès.  
  
## Syntaxe  
  
```  
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### Paramètres  
 `pbstrShortName`  
 \[out\]  Chaîne contenant le nom court de le document.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode retourne le nom de le document sans informations de chemin d'accès.  Le nom court est généralement utilisé dans les boîtes de dialogue.  
  
## Voir aussi  
 [IDebugDocumentTextExternalAuthor, interface](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)