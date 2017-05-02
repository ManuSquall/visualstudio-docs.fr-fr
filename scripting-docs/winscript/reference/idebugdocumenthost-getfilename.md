---
title: "IDebugDocumentHost::GetFileName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetFileName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetFileName"
ms.assetid: b814a848-8a3d-468d-9282-c5c0354b22a1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetFileName
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
 Cette méthode retourne le nom court de le document sans informations de chemin d'accès.  Le nom court est généralement utilisé dans les situations telles que la boîte de dialogue **Enregistrez comme…** .  
  
## Voir aussi  
 [IDebugDocumentHost, interface](../../winscript/reference/idebugdocumenthost-interface.md)