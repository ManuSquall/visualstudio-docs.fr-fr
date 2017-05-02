---
title: "IDebugDocumentTextEvents::onRemoveText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextEvents.onRemoveText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextEvents::onRemoveText"
ms.assetid: c5dfe674-c42f-4e57-9d48-8380d5aa206b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextEvents::onRemoveText
Indique que le texte a été supprimé du document.  
  
## Syntaxe  
  
```  
HRESULT onRemoveText(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToRemove  
);  
```  
  
#### Paramètres  
 `cCharacterPosition`  
 \[in\]  La position de caractère du premier caractère supprimé.  
  
 `cNumToRemove`  
 \[in\]  le nombre de caractères supprimés.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode indique que le texte a été supprimé du document.  
  
## Voir aussi  
 [IDebugDocumentTextEvents, interface](../../winscript/reference/idebugdocumenttextevents-interface.md)   
 [IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)