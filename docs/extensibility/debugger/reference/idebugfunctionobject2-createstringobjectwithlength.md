---
title: "IDebugFunctionObject2::CreateStringObjectWithLength | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CreateStringObjectWithLength"
  - "IDebugFunctionObject2::CreateStringObjectWithLength"
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject2::CreateStringObjectWithLength
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crée un objet chaîne qui a une longueur spécifiée.  
  
## Syntaxe  
  
```cpp#  
HRESULT CreateStringObjectWithLength (  
   LPCOLESTR      pcstrString,  
   UINT           uiLength,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreateStringObjectWithLength (  
   string           pcstrString,  
   uint             uiLength,  
   out IDebugObject ppObject  
);  
```  
  
#### Paramètres  
 `pcstrString`  
 \[in\]  La valeur de chaîne de l'objet String.  
  
 `uiLength`  
 \[in\]  La longueur en octets.  
  
 `ppObject`  
 \[out\]  Retourne un objet d' [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui représente l'objet String nouvellement créée.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)