---
title: "IDebugPropertyField::GetPropertySetter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyField::GetPropertySetter"
helpviewer_keywords: 
  - "IDebugPropertyField::GetPropertySetter (méthode)"
ms.assetid: 744d76fd-2bcc-4917-a040-ce4cc714ef61
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPropertyField::GetPropertySetter
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient la méthode qui définit la propriété.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetPropertySetter(   
   IDebugMethodField** ppField  
);  
```  
  
```c#  
int GetPropertySetter(  
   out IDebugMethodField ppField  
);  
```  
  
#### Paramètres  
 `ppField`  
 \[out\]  Retourne un objet d' [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) représentant la méthode qui définit la propriété.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon retourne un code d'erreur.  
  
## Notes  
 Pour obtenir la méthode qui reçoit la propriété, appelez la méthode d' [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) .  
  
## Voir aussi  
 [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)