---
title: "IDebugDocumentText2::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentText2::GetSize"
helpviewer_keywords: 
  - "IDebugDocumentText2::GetSize"
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentText2::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

extrait la taille du texte à cette position dans le document.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetSize(   
   ULONG* pcNumLines,  
   ULONG* pcNumChars  
);  
```  
  
```c#  
int GetSize(   
   ref uint pcNumLines,  
   ref uint pcNumChars  
);  
```  
  
#### Paramètres  
 `pcNumLines`  
 \[out\]  Retourne le nombre de lignes de texte.  
  
 `pcNumChars`  
 \[out\]  Retourne le nombre de caractères de texte.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 \[C\+\+\] uniquement si une valeur particulière n'est pas souhaité, passez une valeur NULL pour le paramètre.  
  
 \[C\#\] uniquement les deux paramètres doivent être spécifiés.  
  
## Voir aussi  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)