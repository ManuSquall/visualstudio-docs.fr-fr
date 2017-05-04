---
title: "IDebugDocumentHelper::Init | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.Init
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::Init"
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::Init
La méthode d' `Init` initialise un programme d'assistance de document de débogage avec un nom et d'origine.  
  
## Syntaxe  
  
```  
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### Paramètres  
 `pda`  
 \[in\]  L'application de débogage associée à ce document.  
  
 `pszShortName`  
 \[in\]  Une chaîne terminée par le caractère NULL qui contient le nom court de le document.  
  
 `pszLongName`  
 \[in\]  Une chaîne terminée par le caractère NULL qui contient le nom long de le document.  
  
 `docAttr`  
 \[in\]  Spécifie les attributs de document texte.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode initialise un programme d'assistance de document de débogage avec un nom et d'origine.  
  
 Ce document n'apparaît pas dans l'arborescence jusqu'à ce qu' `IDebugDocumentHelper::Attach` soit appelé.  
  
## Voir aussi  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper, interface](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT\_DOC\_ATTR, constantes](../../winscript/reference/text-doc-attr-constants.md)