---
title: "IDebugProcess2::EnumPrograms | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::EnumPrograms"
helpviewer_keywords: 
  - "IDebugProcess2::EnumPrograms"
ms.assetid: f5b7295d-487d-464f-a4c6-d54175b07705
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::EnumPrograms
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Pour récupérer une liste de tous les programmes contenus par ce processus.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnumPrograms(   
   IEnumDebugPrograms2** ppEnum  
);  
```  
  
```c#  
int EnumPrograms(   
   out IEnumDebugPrograms2 ppEnum  
);  
```  
  
#### Paramètres  
 `ppEnum`  
 \[out\]  Retourne un objet d' [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md) qui contient une liste de tous les programmes dans le processus.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)