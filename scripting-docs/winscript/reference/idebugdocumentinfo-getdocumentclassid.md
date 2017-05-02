---
title: "IDebugDocumentInfo::GetDocumentClassId | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentInfo.GetDocumentClassId
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentInfo::GetDocumentClassId"
ms.assetid: 3b858794-2c0c-42ba-b98c-cd820ebace20
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentInfo::GetDocumentClassId
Retourne `CLSID` identificateur le type de document.  
  
## Syntaxe  
  
```  
HRESULT GetDocumentClassId(  
   CLSID*  pclsidDocument  
);  
```  
  
#### Paramètres  
 `pclsidDocument`  
 \[out\]  `CLSID` identificateur le type de document.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode permet le débogueur IDE des visionneuses personnalisés hôte pour ce document.  
  
 Si le document n'a pas de données affichables, la valeur de retour d' `pclsidDocument` est `CLSID_NULL`.  
  
## Voir aussi  
 [IDebugDocumentInfo, interface](../../winscript/reference/idebugdocumentinfo-interface.md)