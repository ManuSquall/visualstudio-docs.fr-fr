---
title: "IDebugDocumentTextEvents::onInsertText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextEvents.onInsertText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextEvents::onInsertText"
ms.assetid: 775881de-497a-47a9-86ab-823d77745a72
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextEvents::onInsertText
Indique que le nouveau texte a été ajouté au document.  
  
## Syntaxe  
  
```  
HRESULT onInsertText(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToInsert  
);  
```  
  
#### Paramètres  
 `cCharacterPosition`  
 \[in\]  La position du caractère où le nouveau texte a été inséré.  
  
 `cNumToInsert`  
 \[in\]  le nombre de caractères qui ont été insérés.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode est généralement appelé par un hôte que progressivement charge le contenu, tels qu'un navigateur web.  
  
## Voir aussi  
 [IDebugDocumentTextEvents, interface](../../winscript/reference/idebugdocumenttextevents-interface.md)   
 [IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)