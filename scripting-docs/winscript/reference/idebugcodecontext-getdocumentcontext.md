---
title: "IDebugCodeContext::GetDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugCodeContext.GetDocumentContext
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugCodeContext::GetDocumentContext"
ms.assetid: 9fe17b65-3a8c-4d21-9b66-0e4ff303af72
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCodeContext::GetDocumentContext
Retourne le contexte de document associé à ce contexte de code.  
  
## Syntaxe  
  
```  
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### Paramètres  
 `ppsc`  
 \[out\]  Le contexte de document associé à ce contexte de code.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Pour les documents texte, la plage de caractère\- position doit inclure du texte pour l'instruction complète.  Cela permet au débogueur IDE pour mettre en surbrillance l'instruction de source actuelle.  
  
## Voir aussi  
 [IDebugCodeContext, interface](../../winscript/reference/idebugcodecontext-interface.md)