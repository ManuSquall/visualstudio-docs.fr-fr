---
title: "IDebugPointerObject::Dereference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerObject::Dereference"
helpviewer_keywords: 
  - "IDebugPointerObject::Dereference (méthode)"
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPointerObject::Dereference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient l'objet désigné.  
  
## Syntaxe  
  
```cpp#  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### Paramètres  
 `dwIndex`  
 \[in\]  Un décalage d'octet simple du début de l'objet indiquée.  
  
 `ppObject`  
 \[out\]  Retourne un objet d' [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant l'objet désigné, plus l'offset le cas échéant.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  Retourne E\_FAIL si cet objet n'indique pas un autre objet.  
  
## Notes  
 L'objet désigné peut être une primitive ou plus d'un type complexe tel qu'une classe ou une structure.  
  
## Voir aussi  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)