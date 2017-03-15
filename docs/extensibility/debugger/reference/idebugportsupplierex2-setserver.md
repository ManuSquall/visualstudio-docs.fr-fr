---
title: "IDebugPortSupplierEx2::SetServer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortSupplierEx2::SetServer"
ms.assetid: 0e8ef194-3a4f-4abf-8382-4607ab3005d1
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugPortSupplierEx2::SetServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

définit le principal serveur pour le fournisseur de port.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetServer(  
   IDebugCoreServer2* pServer  
);  
```  
  
```c#  
int SetServer(  
   IDebugCoreServer2 pServer  
);  
```  
  
#### Paramètres  
 `pServer`  
 principal serveur à définir pour le fournisseur de port.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugPortSupplierEx2](../../../extensibility/debugger/reference/idebugportsupplierex2.md)