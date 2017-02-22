---
title: "IDebugExtendedField::IsClosedType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IsClosedType"
  - "IDebugExtendedField::IsClosedType"
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExtendedField::IsClosedType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

détermine si le champ représente un type fermé.  
  
## Syntaxe  
  
```cpp#  
HRESULT IsClosedType(  
   void  
);  
```  
  
```c#  
int IsClosedType();  
```  
  
## Valeur de retour  
 Si le champ est un type fermé, retourne `S_OK`; sinon, retourne `S_FALSE`.  
  
## Voir aussi  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)