---
title: "IJsDebugFrame::GetDocumentPositionWithName, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetDocumentPositionWithName
apilocation: jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetDocumentPositionWithName, m&#233;thode
Retourne la position actuelle de ce frame de pile dans le document de niveau utilisateur.  
  
## Syntaxe  
  
```  
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### Paramètres  
 `pDocumentName`  
 \[out\] Pour les scripts statiques, une URL à documenter.  Pour les scripts dynamiques, un nom contenant le type de script \(par exemple, le code eval, le code de fonction, etc.\) est retourné.  
  
 `pLine`  
 \[out\] Position de la ligne de base 1 dans le document.  
  
 `pColumn`  
 \[out\] Position de la ligne de base 1 dans le document.  
  
## Valeur de retour  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsDebugFrame, interface](../../winscript/reference/ijsdebugframe-interface.md)