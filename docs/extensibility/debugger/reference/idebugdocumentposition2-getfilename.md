---
title: "IDebugDocumentPosition2::GetFileName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2::GetFileName"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::GetFileName"
ms.assetid: d713635e-088f-465b-b26d-00ac971c9e86
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentPosition2::GetFileName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le nom du fichier source contenant la position de document.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetFileName(   
   BSTR* pbstrFileName  
);  
```  
  
```c#  
int GetFileName(   
   out string pbstrFileName  
);  
```  
  
#### Paramètres  
 `pbstrFileName`  
 \[out\]  Retourne le nom de fichier du fichier source.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Un fichier source peut ne pas avoir un nom de fichier \(fichier source peut ne pas exister sur le disque, par exemple\).  
  
## Voir aussi  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)