---
title: "IDebugField::GetAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetAddress"
helpviewer_keywords: 
  - "IDebugField::GetAddress (méthode)"
ms.assetid: 6981bf03-66ef-4bf9-87ea-f6c9624486cb
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::GetAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette méthode obtient l'adresse de débogage d'un champ.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetAddress(   
   IDebugAddress** ppAddress  
);  
```  
  
```c#  
int GetAddress(  
   out IDebugAddress ppAddress  
);  
```  
  
#### Paramètres  
 `ppAddress`  
 \[out\]  Retourne l'adresse comme un objet d' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, le code d'erreur.  
  
## Voir aussi  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)