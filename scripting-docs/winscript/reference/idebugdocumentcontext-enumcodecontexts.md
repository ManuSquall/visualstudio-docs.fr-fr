---
title: "IDebugDocumentContext::EnumCodeContexts | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentContext.EnumCodeContexts
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentContext::EnumCodeContexts"
ms.assetid: fb0aa64e-c458-4ef1-bcd8-5cebdc972549
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentContext::EnumCodeContexts
Énumère les contextes de code associés à ce contexte de document.  
  
## Syntaxe  
  
```  
HRESULT EnumCodeContexts(  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### Paramètres  
 `ppescc`  
 \[out\]  Les contextes de code associés à ce contexte de document.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Un document est généralement associé à un seul contexte de code, à moins que le document ne soit un fichier Include ou un modèle.  
  
## Voir aussi  
 [IDebugDocumentContext, interface](../../winscript/reference/idebugdocumentcontext-interface.md)