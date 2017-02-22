---
title: "IDebugPropertyField::GetPropertyGetter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyField::GetPropertyGetter"
helpviewer_keywords: 
  - "IDebugPropertyField::GetPropertyGetter (méthode)"
ms.assetid: ab9f861a-42ad-4a82-9ae6-2606176f755a
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPropertyField::GetPropertyGetter
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient la méthode qui reçoit la propriété.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetPropertyGetter(   
   IDebugMethodField** ppField  
);  
```  
  
```cpp#  
int GetPropertyGetter(  
   out IDebugMethodField ppField  
);  
```  
  
#### Paramètres  
 `ppField`  
 \[out\]  Retourne un objet d' [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) représentant la méthode qui obtient la propriété.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Pour obtenir la méthode qui définit la propriété, appelez d' [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md) la méthode.  
  
## Voir aussi  
 [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)   
 [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)