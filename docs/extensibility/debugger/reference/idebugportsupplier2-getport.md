---
title: "IDebugPortSupplier2::GetPort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2::GetPort"
helpviewer_keywords: 
  - "IDebugPortSupplier2::GetPort"
ms.assetid: d55d5055-7386-4037-bf22-4c3e434a99ca
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortSupplier2::GetPort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient un port d'un fournisseur de port.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetPort(   
   REFGUID       guidPort,  
   IDebugPort2** ppPort  
);  
```  
  
```c#  
int GetPort(   
   ref Guid        guidPort,  
   out IDebugPort2 ppPort  
);  
```  
  
#### Paramètres  
 `guidPort`  
 \[in\]  identificateur global unique \(GUID\) du port.  
  
 `ppPort`  
 \[out\]  Retourne un objet d' [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) qui représente le port.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Retourne `E_PORTSUPPLIER_NO_PORT` si aucun port n'existe avec l'identificateur donné.  
  
## Voir aussi  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)