---
title: "IDebugDocumentText::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetSize
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetSize"
ms.assetid: 9da53856-613a-44b2-a84c-99454a2a1548
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetSize
Retourne le nombre de lignes et le nombre de caractères du document.  
  
## Syntaxe  
  
```  
HRESULT GetSize(  
   ULONG*  pcNumLines,  
   ULONG*  pcNumChars  
);  
```  
  
#### Paramètres  
 `pcNumLines`  
 \[out\]  Nombre de lignes de le document.  Si ce paramètre est NULL, la méthode ne retourne pas de valeur.  
  
 `pcNumChars`  
 \[out\]  Nombre de caractères du document.  Si ce paramètre est NULL, la méthode ne retourne pas de valeur.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode retourne le nombre de lignes et le nombre de caractères du document.  
  
## Voir aussi  
 [IDebugDocumentText, interface](../../winscript/reference/idebugdocumenttext-interface.md)