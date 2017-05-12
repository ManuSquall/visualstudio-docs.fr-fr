---
title: "IDebugDocumentHost::NotifyChanged | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.NotifyChanged
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::NotifyChanged"
ms.assetid: 33a4a54f-3bcb-4422-b3c0-bdbf46590f34
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::NotifyChanged
Avertit l'hôte que le fichier source du document a été enregistré et que son contenu doit être actualisé.  
  
## Syntaxe  
  
```  
HRESULT NotifyChanged();  
```  
  
#### Paramètres  
 Cette méthode n'accepte pas de paramètres.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode avertit l'hôte que le fichier source du document a été enregistré et que son contenu doit être actualisé.  
  
## Voir aussi  
 [IDebugDocumentHost, interface](../../winscript/reference/idebugdocumenthost-interface.md)