---
title: "IDebugFunctionObject::CreateArrayObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreateArrayObject"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreateArrayObject (méthode)"
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crée un objet table.  Ce tableau peut contenir des valeurs de primitif ou d'instance de l'objet.  
  
## Syntaxe  
  
```cpp#  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### Paramètres  
 `ot`  
 \[in\]  Spécifie une valeur de l'énumération d' [OBJECT\_TYPE](../../../extensibility/debugger/reference/object-type.md) indiquant le type du nouvel objet table.  
  
 `pClassField`  
 \[in\]  Un objet d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) qui représente la classe d'un objet, si vous créez un tableau de valeurs d'une instance d'objet.  Si vous créez un tableau d'objets primitifs, ce paramètre est une valeur NULL.  
  
 `dwRank`  
 \[in\]  Le rang ou le nombre de dimensions du tableau.  
  
 `dwDims`  
 \[in\]  Les tailles de chaque dimension du tableau.  
  
 `dwLowBounds`  
 \[in\]  l'origine de chaque dimension \(en général 0 ou 1\).  
  
 `ppObject`  
 \[out\]  Retourne un objet d' [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant le tableau nouvellement créée.  C'est précisément un objet d' [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Appelez cette méthode pour créer un objet qui représente un paramètre de tableau à la fonction qui est représentée par l'interface d' [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
## Voir aussi  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)