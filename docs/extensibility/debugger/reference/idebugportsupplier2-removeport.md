---
title: "IDebugPortSupplier2::RemovePort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2::RemovePort"
helpviewer_keywords: 
  - "IDebugPortSupplier2::RemovePort"
ms.assetid: f5c1fbf2-9084-46f2-a682-7db963928df2
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPortSupplier2::RemovePort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Supprime un port.  
  
## Syntaxe  
  
```cpp#  
HRESULT RemovePort(   
   IDebugPort2* pPort  
);  
```  
  
```c#  
int RemovePort(   
   IDebugPort2 pPort  
);  
```  
  
#### Paramètres  
 `pPort`  
 \[in\]  un objet d' [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) qui représente le port à supprimer.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode supprime le port de la liste interne du fournisseur de port de ports actifs.  
  
## Voir aussi  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)