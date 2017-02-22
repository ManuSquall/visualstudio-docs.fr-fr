---
title: "IDebugProperty2::GetReference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetReference"
helpviewer_keywords: 
  - "IDebugProperty2::GetReference (méthode)"
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty2::GetReference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne une référence à la valeur de la propriété.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetReference(  
   IDebugReference2** ppReference  
);  
```  
  
```c#  
int GetReference(  
   out IDebugReference2 ppReference  
);  
```  
  
#### Paramètres  
 `ppRererence`  
 \[out\]  Retourne un objet d' [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) représentant une référence à la valeur de la propriété.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur, en général `E_NOTIMPL` ou `E_GETREFERENCE_NO_REFERENCE`.  
  
## Voir aussi  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)