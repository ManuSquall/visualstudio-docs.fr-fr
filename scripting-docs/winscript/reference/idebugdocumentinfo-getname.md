---
title: "IDebugDocumentInfo::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentInfo.GetName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentInfo::GetName"
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentInfo::GetName
Retourne le nom spécifié de document.  
  
## Syntaxe  
  
```  
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### Paramètres  
 `dnt`  
 \[in\]  le type de nom de document à retourner.  
  
 `pbstrName`  
 \[out\]  chaîne contenant le nom.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Le nom spécifié de document n'est pas connu.|  
  
## Notes  
 Cette méthode retourne le nom spécifié de document.  
  
## Voir aussi  
 [IDebugDocumentInfo, interface](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [DOCUMENTNAMETYPE, énumération](../../winscript/reference/documentnametype-enumeration.md)