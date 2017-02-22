---
title: "IDebugPort2::GetPortName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPort2::GetPortName"
helpviewer_keywords: 
  - "IDebugPort2::GetPortName"
ms.assetid: 4478b3d5-aa30-4105-8d05-e3bae2f8917a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPort2::GetPortName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le nom de port.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetPortName(   
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetPortName(   
   out string pbstrName  
);  
```  
  
#### Paramètres  
 `pbstrName`  
 \[out\]  Retourne le nom du port.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)