---
title: "IDebugExpressionEvaluator2::SetIDebugIDECallback | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator2::SetIDebugIDECallback"
  - "SetIDebugIDECallback"
ms.assetid: f01c40ad-ef4b-477b-8304-602c6972bc88
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionEvaluator2::SetIDebugIDECallback
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

permet à un moteur de débogage pour passer un rappel à l'évaluateur d'expression pendant l'initialisation.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetIDebugIDECallback (  
   IDebugIDECallback * pCallback  
);  
```  
  
```c#  
int SetIDebugIDECallback (  
   IDebugIDECallback pCallback  
);  
```  
  
#### Paramètres  
 `pCallback`  
 \[in\]  interface pour le rappel.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)