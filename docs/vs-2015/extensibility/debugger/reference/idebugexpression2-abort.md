---
title: IDebugExpression2::Abort | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35ddf670fde7d5940bdbd4018a0b578f867de0f6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932635"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode annule l’évaluation de l’expression asynchrone comme démarrée par un appel à la [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Abort(  
   void  
);  
```  
  
```csharp  
int Abort();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Lors de l’évaluation de l’expression asynchrone est annulée, ne pas envoyé un [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) événement au rappel d’événement passé à la [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) ou [attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md) méthodes.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)

