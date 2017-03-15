---
title: "IDebugFunctionObject::CreatePrimitiveObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreatePrimitiveObject"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreatePrimitiveObject (méthode)"
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugFunctionObject::CreatePrimitiveObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crée un objet de données primitives, tel qu'un entier simple.  
  
## Syntaxe  
  
```cpp#  
HRESULT CreatePrimitiveObject(   
   OBJECT_TYPE    ot,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreatePrimitiveObject(  
   enum_OBJECT_TYPE ot,   
   out IDebugObject ppObject  
);  
```  
  
#### Paramètres  
 `ot`  
 \[in\]  Une valeur de l'énumération d' [OBJECT\_TYPE](../../../extensibility/debugger/reference/object-type.md) représentant le type de primitive à créer.  
  
 `ppObject`  
 \[out\]  Retourne [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant l'objet nouvellement créé.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Appelez cette méthode pour créer un objet qui représente un objet primitif qui est un paramètre de la fonction qui est représentée par l'interface d' [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  Par exemple, si la chaîne d'expression « myString \(5\) », cette méthode est utilisée pour créer un objet représentant les 5. entiers.  
  
## Voir aussi  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)