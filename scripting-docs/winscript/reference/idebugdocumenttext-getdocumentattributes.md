---
title: "IDebugDocumentText::GetDocumentAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetDocumentAttributes
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetDocumentAttributes"
ms.assetid: 8c544ca1-8db4-4bca-973e-09315d9a0ee5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetDocumentAttributes
Retourne les attributs du document.  
  
## Syntaxe  
  
```  
HRESULT GetDocumentAttributes(  
   TEXT_DOC_ATTR*  ptextdocattr  
);  
```  
  
#### Paramètres  
 `ptextdocattr`  
 \[out\]  Les attributs de texte du document.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode retourne les attributs du document.  
  
## Voir aussi  
 [IDebugDocumentText, interface](../../winscript/reference/idebugdocumenttext-interface.md)   
 [TEXT\_DOC\_ATTR, constantes](../../winscript/reference/text-doc-attr-constants.md)