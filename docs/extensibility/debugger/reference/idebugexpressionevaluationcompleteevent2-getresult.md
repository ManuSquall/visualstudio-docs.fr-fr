---
title: "IDebugExpressionEvaluationCompleteEvent2::GetResult | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluationCompleteEvent2::GetResult"
helpviewer_keywords: 
  - "IDebugExpressionEvaluationCompleteEvent2::GetResult"
ms.assetid: d9ad3e22-b6b2-421e-9a43-6bb8c70d12a9
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugExpressionEvaluationCompleteEvent2::GetResult
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le résultat de l'évaluation d'une expression.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetResult(   
   IDebugProperty2** ppResult  
);  
```  
  
```c#  
int GetResult(   
   out IDebugProperty2 ppResult  
);  
```  
  
#### Paramètres  
 `ppResult`  
 \[out\]  Retourne un objet d' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui représente le résultat de l'évaluation d'une expression.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 l'objet retourné d' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) contient la valeur de l'expression évaluée.  Notez que cette valeur peut être une valeur complexe telle qu'un tableau mais le résultat final doit être un type numérique ou une valeur de chaîne qui est présenté à l'utilisateur.  
  
## Voir aussi  
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)