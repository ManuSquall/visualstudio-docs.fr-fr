---
title: "IDebugArrayObject2::HasBaseIndices | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HasBaseIndices"
  - "IDebugArrayObject2::HasBaseIndices"
ms.assetid: 51a5d145-ea53-422c-b5cf-c800cf64b8e6
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugArrayObject2::HasBaseIndices
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Détermine si le tableau a les index de base \(limite inférieure\) définis.  
  
## Syntaxe  
  
```cpp#  
HRESULT HasBaseIndices (  
   BOOL* pfHasBaseIndices  
);  
```  
  
```c#  
int HasBaseIndices (  
   out bool pfHasBaseIndices  
);  
```  
  
#### Paramètres  
 `pfHasBaseIndices`  
 \[out\]  TRUE à spécifier que le tableau présente les index de base \(limite inférieure\) ; sinon, FALSE.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.