---
title: "IDebugDocumentHelper::SetLongName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.SetLongName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::SetLongName"
ms.assetid: b6199e5d-9b54-43a2-9775-214b8d022607
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::SetLongName
Définit le nom long de le document.  
  
## Syntaxe  
  
```  
HRESULT SetLongName(  
   LPCOLESTR  pszLongName  
);  
```  
  
#### Paramètres  
 `pszLongName`  
 \[in\]  Une chaîne terminée par le caractère NULL qui contient le nom long de le document.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode définit un nouveau nom long de le document.  
  
## Voir aussi  
 [IDebugDocumentHelper, interface](../../winscript/reference/idebugdocumenthelper-interface.md)