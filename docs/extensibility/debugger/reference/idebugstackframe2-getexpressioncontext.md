---
title: IDebugStackFrame2::GetExpressionContext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3953f02e1795f2b8b4b6fbfc6536ac83c16ce205
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934130"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
Obtient un contexte d’évaluation pour l’évaluation d’expression dans le contexte actuel d’un frame de pile et le thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExpressionContext (   
   IDebugExpressionContext2** ppExprCxt  
);  
```  
  
```csharp  
int GetExpressionContext (   
   out IDebugExpressionContext2 ppExprCxt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppExprCxt`  
 [out] Retourne un [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) objet qui représente un contexte pour l’évaluation de l’expression.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 En règle générale, un contexte d’évaluation d’expression peut être considéré en tant qu’étendue pour effectuer l’évaluation de l’expression. Appelez le [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) méthode pour analyser une expression puis appelez résultant [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) méthodes pour évaluer l’expression analysée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)