---
title: "IDebugStackFrame::GetDescriptionString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetDescriptionString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetDescriptionString"
ms.assetid: a2ddc069-c440-4dee-98dc-ab7c78773b94
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetDescriptionString
Retourne une description textuelle courte ou plus longue du frame de pile.  
  
## Syntaxe  
  
```  
HRESULT GetDescriptionString(  
   BOOL   fLong,  
   BSTR*  pbstrDescription  
);  
```  
  
#### Paramètres  
 `fLong`  
 \[in\]  La balise, où `TRUE` retourne une description plus longue et `FALSE` retourne une description courte.  
  
 `pbstrDescription`  
 \[out\]  la description du frame de pile.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 En général, si `fLong` est `FALSE`, cette méthode fournit uniquement le nom de la fonction associée au frame de pile.  Lorsque `fLong` est `TRUE`, cette méthode peut également fournir des paramètres de fonction et d'autres informations pertinentes.  
  
## Voir aussi  
 [IDebugStackFrame, interface](../../winscript/reference/idebugstackframe-interface.md)