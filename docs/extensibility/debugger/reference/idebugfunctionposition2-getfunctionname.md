---
title: "IDebugFunctionPosition2::GetFunctionName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionPosition2::GetFunctionName"
helpviewer_keywords: 
  - "IDebugFunctionPosition2::GetFunctionName"
ms.assetid: eb7a348e-a7f5-4f25-be68-80482d5482a8
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugFunctionPosition2::GetFunctionName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le nom de la fonction laquelle cette position indique.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetFunctionName(   
   BSTR* pbstrFunctionName  
);  
```  
  
```c#  
int GetFunctionName(  
   out string pbstrFunctionName  
);  
```  
  
#### Paramètres  
 `pbstrFunctionName`  
 \[out\]  Retourne le nom de la fonction.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)