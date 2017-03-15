---
title: "IDebugPortSupplier2::AddPort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2::AddPort"
helpviewer_keywords: 
  - "IDebugPortSupplier2::AddPort"
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortSupplier2::AddPort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ajoute un port.  
  
## Syntaxe  
  
```cpp#  
HRESULT AddPort(   
   IDebugPortRequest2* pRequest,  
   IDebugPort2**       ppPort  
);  
```  
  
```c#  
int AddPort(   
   IDebugPortRequest2 pRequest,  
   out IDebugPort2    ppPort  
);  
```  
  
#### Paramètres  
 `pRequest`  
 \[in\]  un objet d' [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) qui décrit le port à ajouter.  
  
 `ppPort`  
 \[out\]  Retourne un objet d' [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) qui représente le port.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode crée en fait le port demandé ainsi que l'ajoutant à la liste interne du fournisseur de port de ports actifs.  La méthode d' [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) peut être d'abord appelée pour éviter des délais longs possibles.  
  
## Voir aussi  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)