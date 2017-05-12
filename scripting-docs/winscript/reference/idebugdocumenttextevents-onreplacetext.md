---
title: "IDebugDocumentTextEvents::onReplaceText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextEvents.onReplaceText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextEvents::onReplaceText"
ms.assetid: 3cb053c4-1f7f-4aed-aee6-f8a9e9e69d29
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextEvents::onReplaceText
Indique que le texte a été remplacé.  
  
## Syntaxe  
  
```  
HRESULT onReplaceText(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToReplace  
);  
```  
  
#### Paramètres  
 `cCharacterPosition`  
 \[in\]  La position de caractère du premier caractère remplacé.  
  
 `cNumToReplace`  
 \[in\]  Le nombre de caractères de substitution.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode indique que le texte a été remplacé.  
  
## Voir aussi  
 [IDebugDocumentTextEvents, interface](../../winscript/reference/idebugdocumenttextevents-interface.md)