---
title: "IDebugPointerObject3::GetPointerAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetPointerAddress"
  - "IDebugPointerObject3::GetPointerAddress"
ms.assetid: 4cc5af04-9e70-420d-8230-ef3108df6d51
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPointerObject3::GetPointerAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère l'adresse du pointeur.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetPointerAddress (  
   UINT64* puAddress  
);  
```  
  
```c#  
int GetPointerAddress (  
   out ulong puAddress  
);  
```  
  
#### Paramètres  
 `puAddress`  
 \[out\]  Retourne l'adresse du pointeur.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)