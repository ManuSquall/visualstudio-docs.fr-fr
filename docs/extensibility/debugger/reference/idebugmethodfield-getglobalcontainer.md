---
title: "IDebugMethodField::GetGlobalContainer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::GetGlobalContainer"
helpviewer_keywords: 
  - "IDebugMethodField::GetGlobalContainer (méthode)"
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::GetGlobalContainer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le conteneur global de la méthode.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetGlobalContainer(  
   IDebugClassField** ppClass  
);  
```  
  
```c#  
int GetGlobalContainer(  
   out IDebugClassField ppClass  
);  
```  
  
#### Paramètres  
 `ppClass`  
 \[out\]  Retourne [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) représentant le module dans lequel cette méthode est définie.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 L'objet retourné d' [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) représente le module entier et est un objet artificiel, c. autrement dit., le module n'a pas une classe réelle mais il peut être représenté par un objet d' `IDebugClassField` , ce qui permet aux éléments individuels du module à énumérer et être découvert.  
  
## Voir aussi  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)