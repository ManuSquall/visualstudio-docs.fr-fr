---
title: "IDebugProcess2::GetPort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetPort"
helpviewer_keywords: 
  - "IDebugProcess2::GetPort"
ms.assetid: e39b6e5a-64eb-48cf-a53d-da4fdb968e2d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::GetPort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le port que le processus s'exécute.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetPort(   
   IDebugPort2** ppPort  
);  
```  
  
```c#  
int GetPort(   
   out IDebugPort2 ppPort  
);  
```  
  
#### Paramètres  
 `ppPort`  
 \[out\]  Retourne un objet d' [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) qui représente le port sur lequel le processus a été lancé.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)