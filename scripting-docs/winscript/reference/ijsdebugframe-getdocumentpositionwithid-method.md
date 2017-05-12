---
title: "IJsDebugFrame::GetDocumentPositionWithId, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetDocumentPositionWithId
apilocation: jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetDocumentPositionWithId, m&#233;thode
Retourne la position actuelle de ce frame de pile dans le document de niveau utilisateur.  
  
## Syntaxe  
  
```  
HRESULT GetDocumentPositionWithId(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### Paramètres  
 `pDocumentId`  
 \[out\] Identificateur unique d'un document source \(pointeur vers IDebugDocumentText\).  
  
 `pCharacterOffset`  
 \[out\] Décalage de caractère de base zéro depuis le début du script.  
  
 `pStatementCharCount`  
 \[out\] Longueur de l'instruction actuelle, qui commence à \*pCharacterOffset, en caractères.  
  
## Valeur de retour  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsDebugFrame, interface](../../winscript/reference/ijsdebugframe-interface.md)