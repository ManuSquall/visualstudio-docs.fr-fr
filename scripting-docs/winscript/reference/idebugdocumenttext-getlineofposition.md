---
title: "IDebugDocumentText::GetLineOfPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetLineOfPosition
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetLineOfPosition"
ms.assetid: fe8d4802-ea16-49ca-8973-89dcaf6c915b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetLineOfPosition
Retourne le numéro de ligne et, éventuellement, le décalage de caractère dans la ligne correspondant à la caractère\- position donnée.  
  
## Syntaxe  
  
```  
HRESULT GetLineOfPosition(  
   ULONG   cCharacterPosition,  
   ULONG*  pcLineNumber,  
   ULONG*  pcCharacterOffsetInLine  
);  
```  
  
#### Paramètres  
 `cCharacterPosition`  
 \[in\]  Position de départ de la plage de la position du caractère.  
  
 `pcLineNumber`  
 \[out\]  Le numéro de ligne de la plage.  
  
 `pcCharacterOffsetInLine`  
 \[in, out\]  L'offset de caractères de la plage dans la ligne `pcLineNumber`.  Si ce paramètre est `NULL`, la méthode ne retourne pas de valeur.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode retourne le numéro de ligne et, éventuellement, le décalage de caractère dans la ligne correspondant à la caractère\- position donnée.  
  
## Voir aussi  
 [IDebugDocumentText, interface](../../winscript/reference/idebugdocumenttext-interface.md)