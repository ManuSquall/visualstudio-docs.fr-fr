---
title: "IDebugArrayField::GetElementType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayField::GetElementType"
helpviewer_keywords: 
  - "IDebugArrayField::GetElementType (méthode)"
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugArrayField::GetElementType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le type d'élément du tableau.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetElementType(   
   IDebugField** ppType  
);  
```  
  
```c#  
int GetElementType(  
   out IDebugField ppType  
);  
```  
  
#### Paramètres  
 `ppType`  
 \[out\]  Retourne un objet d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) qui décrit le type d'élément.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 L'objet d' [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) suppose que tous les éléments du tableau sont du même type.  
  
## Voir aussi  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)