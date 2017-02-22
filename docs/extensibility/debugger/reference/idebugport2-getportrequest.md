---
title: "IDebugPort2::GetPortRequest | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPort2::GetPortRequest"
helpviewer_keywords: 
  - "IDebugPort2::GetPortRequest"
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPort2::GetPortRequest
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient la description d'un port qui a été utilisé précédemment pour créer le port \(si disponible\).  
  
## Syntaxe  
  
```cpp#  
HRESULT GetPortRequest(   
   IDebugPortRequest2** ppRequest  
);  
```  
  
```c#  
int GetPortRequest(   
   out IDebugPortRequest2 ppRequest  
);  
```  
  
#### Paramètres  
 `ppRequest`  
 \[out\]  Retourne un objet d' [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) représentant la requête utilisée pour créer le port.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Retourne `E_PORT_NO_REQUEST` si un port n'a pas été créé à l'aide d'une demande de port d' [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) .  
  
## Voir aussi  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Ajouter un port](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)