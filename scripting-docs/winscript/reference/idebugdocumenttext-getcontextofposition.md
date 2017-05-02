---
title: "IDebugDocumentText::GetContextOfPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetContextOfPosition
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetContextOfPosition"
ms.assetid: 86560853-d9b1-499a-a1b5-ea06aa1f1f5c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetContextOfPosition
Crée un objet de contexte de document qui correspond à la plage fourni de la position du caractère.  
  
## Syntaxe  
  
```  
HRESULT GetContextOfPosition(  
   ULONG                    cCharacterPosition,  
   ULONG                    cNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### Paramètres  
 `cCharacterPosition`  
 \[in\]  Position de départ de la plage de la position du caractère.  
  
 `cNumChars`  
 \[in\]  Nombre de caractères de la plage.  
  
 `ppsc`  
 \[out\]  L'objet de contexte de document qui correspond à la plage spécifiée de la position du caractère.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode crée un objet de contexte de document qui correspond à la plage fourni de la position du caractère.  
  
## Voir aussi  
 [IDebugDocumentText, interface](../../winscript/reference/idebugdocumenttext-interface.md)