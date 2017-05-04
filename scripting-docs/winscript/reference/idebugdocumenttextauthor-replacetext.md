---
title: "IDebugDocumentTextAuthor::ReplaceText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextAuthor.ReplaceText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextAuthor::ReplaceText"
ms.assetid: f89304e6-5be0-45a5-947d-2c59c3c0a05e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextAuthor::ReplaceText
Remplace le texte dans le document.  
  
## Syntaxe  
  
```  
HRESULT ReplaceText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToReplace,  
   OLECHAR  pcharText[]  
);  
```  
  
#### Paramètres  
 `cCharacterPosition`  
 \[in\]  Position de départ de la plage de caractères à remplacer.  
  
 `cNumToReplace`  
 \[in\]  Nombre de caractères à remplacer.  
  
 `pcharText[]`  
 \[in\]  Une mémoire tampon qui contient les nouveaux caractères pour remplacer les caractères anciens.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode remplace le texte dans le document.  
  
## Voir aussi  
 [IDebugDocumentTextAuthor, interface](../../winscript/reference/idebugdocumenttextauthor-interface.md)