---
title: "IDebugDocumentTextEvents::onUpdateTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextEvents.onUpdateTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextEvents::onUpdateTextAttributes"
ms.assetid: 24a6d409-3137-4a7a-ac24-0955c109902f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextEvents::onUpdateTextAttributes
Indique que les attributs du texte associés à la plage sous\-jacent de la position du caractère ont changé.  
  
## Syntaxe  
  
```  
HRESULT onUpdateTextAttributes(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToUpdate  
);  
```  
  
#### Paramètres  
 `cCharacterPosition`  
 \[in\]  La position de caractère du premier caractère que les attributs ont changé.  
  
 `cNumToUpdate`  
 \[in\]  Le nombre de caractères de la plage.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode indique que les attributs du texte associés à la plage sous\-jacent de la position du caractère ont changé.  
  
## Voir aussi  
 [IDebugDocumentTextEvents, interface](../../winscript/reference/idebugdocumenttextevents-interface.md)