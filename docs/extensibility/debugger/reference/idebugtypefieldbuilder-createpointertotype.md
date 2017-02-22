---
title: "IDebugTypeFieldBuilder::CreatePointerToType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CreatePointerToType"
  - "IDebugTypeFieldBuilder::CreatePointerToType"
ms.assetid: 73966e8a-b643-43e0-9b4e-0aa4b402ebbe
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugTypeFieldBuilder::CreatePointerToType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crée un pointeur vers le type spécifié.  
  
## Syntaxe  
  
```cpp#  
HRESULT CreatePointerToType(  
   IDebugField*  pTypeField,  
   IDebugField** pPtrToTypeField  
);  
```  
  
```c#  
int CreatePointerToType(  
   IDebugField     pTypeField,  
   out IDebugField pPtrToTypeField  
);  
```  
  
#### Paramètres  
 `pTypeField`  
 \[in\]  Type à lire.  il est représenté par l'interface d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
 `pPtrToTypeField`  
 \[out\]  Retourne le pointeur représenté par un objet **d'IDebugField** .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)