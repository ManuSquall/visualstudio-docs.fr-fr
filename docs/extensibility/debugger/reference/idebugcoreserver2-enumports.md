---
title: "IDebugCoreServer2::EnumPorts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2::EnumPorts"
helpviewer_keywords: 
  - "IDebugCoreServer2::EnumPorts"
ms.assetid: 3d98dfd0-614f-4d68-90c6-8a9b9cab66f1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCoreServer2::EnumPorts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

extrait une liste de tous les ports disponibles.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnumPorts(   
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```c#  
int EnumPorts(   
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### Paramètres  
 `ppEnum`  
 \[out\]  Retourne un objet d' [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) qui contient une liste de tous les ports de tous les fournisseurs de port.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)