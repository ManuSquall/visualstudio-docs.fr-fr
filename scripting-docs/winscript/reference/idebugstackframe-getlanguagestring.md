---
title: "IDebugStackFrame::GetLanguageString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetLanguageString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetLanguageString"
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetLanguageString
Retourne une description textuelle courte ou longue du langage.  
  
## Syntaxe  
  
```  
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### Paramètres  
 `fLong`  
 \[in\]  La balise, où `TRUE` retourne une description plus longue et `FALSE` retourne une description courte.  
  
 `pbstrLanguage`  
 \[out\]  la description du langage.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 En général, si `fLong` est `FALSE`, cette méthode fournit uniquement le nom du langage associé au frame de pile.  Lorsque `fLong` est `TRUE`, cette méthode peut fournir une description complète de produit.  
  
## Voir aussi  
 [IDebugStackFrame, interface](../../winscript/reference/idebugstackframe-interface.md)