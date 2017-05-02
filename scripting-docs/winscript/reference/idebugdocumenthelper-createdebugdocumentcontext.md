---
title: "IDebugDocumentHelper::CreateDebugDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.CreateDebugDocumentContext
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::CreateDebugDocumentContext"
ms.assetid: aa4ec691-9fb1-4da7-8085-b40d8a062467
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::CreateDebugDocumentContext
Crée un débogage le contexte de document.  
  
## Syntaxe  
  
```  
HRESULT CreateDebugDocumentContext(  
   ULONG                    iCharPos,  
   ULONG                    cChars,  
   IDebugDocumentContext**  ppddc  
);  
```  
  
#### Paramètres  
 `iCharPos`  
 \[in\]  emplacement du début du contenu de document de débogage.  
  
 `cChars`  
 \[in\]  Nombre de caractères du contexte.  
  
 `ppddc`  
 \[out\]  Les nouveaux debug le contexte de document.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode permet à l'hôte pour créer un nouveau debug le contexte de document.  
  
## Voir aussi  
 [IDebugDocumentHelper, interface](../../winscript/reference/idebugdocumenthelper-interface.md)