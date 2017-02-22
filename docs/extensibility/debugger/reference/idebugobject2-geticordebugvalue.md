---
title: "IDebugObject2::GetICorDebugValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::GetICorDebugValue"
helpviewer_keywords: 
  - "IDebugObject2::GetICorDebugValue (méthode)"
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugObject2::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient un objet de code managé représentant la valeur associée à cet objet.  
  
## Syntaxe  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```c#  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### Paramètres  
 `ppUnk`  
 \[out\]  interface d' `IUnknown` qui représente le ce alias.  Cette interface peut être interrogé pour l'interface d' `ICorDebugValue` .  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 L'objet d' `ICorDebugValue` est une interface du common langage runtime qui représente une valeur.  
  
## Voir aussi  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)