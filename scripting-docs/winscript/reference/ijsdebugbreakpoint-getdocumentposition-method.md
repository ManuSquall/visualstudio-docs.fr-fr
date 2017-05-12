---
title: "IJsDebugBreakPoint::GetDocumentPosition, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.GetDocumentPosition
apilocation: jscript9diag.dll
ms.assetid: 886df8ba-a59a-48a7-87f2-3b669e71528f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugBreakPoint::GetDocumentPosition, m&#233;thode
Retourne la position de l'instruction où le point d'arrêt a été lié.  
  
## Syntaxe  
  
```  
HRESULT GetDocumentPosition(  
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
 [IJsDebugBreakPoint, interface](../../winscript/reference/ijsdebugbreakpoint-interface.md)