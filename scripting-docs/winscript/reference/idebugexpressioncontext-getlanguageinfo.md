---
title: "IDebugExpressionContext::GetLanguageInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionContext.GetLanguageInfo
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpressionContext::GetLanguageInfo"
ms.assetid: 35e25662-0b2a-4c3f-bce4-f01726bc04a8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionContext::GetLanguageInfo
Retourne un nom et un GUID pour le langage qui possède ce contexte.  
  
## Syntaxe  
  
```  
HRESULT GetLanguageInfo(  
   BSTR*  pbstrLanguageName,  
   GUID*  pLanguageID  
);  
```  
  
#### Paramètres  
 `pbstrLanguageName`  
 \[out\]  le nom du langage.  
  
 `pLanguageID`  
 \[out\]  ID unique du langage.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode retourne un nom et un GUID pour le langage qui possède ce contexte.  
  
## Voir aussi  
 [IDebugExpressionContext, interface](../../winscript/reference/idebugexpressioncontext-interface.md)