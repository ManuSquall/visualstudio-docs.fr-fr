---
title: IDebugExpressionEvaluationCompleteEvent2::GetResult | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
ms.assetid: d9ad3e22-b6b2-421e-9a43-6bb8c70d12a9
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e9b1bf5b24a1e8b0e9ea623eb749827b2e8a988
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493055"
---
# <a name="idebugexpressionevaluationcompleteevent2getresult"></a>IDebugExpressionEvaluationCompleteEvent2::GetResult
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugExpressionEvaluationCompleteEvent2::GetResult](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult).  
  
Obtient le résultat de l’évaluation de l’expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetResult(   
   IDebugProperty2** ppResult  
);  
```  
  
```csharp  
int GetResult(   
   out IDebugProperty2 ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppResult`  
 [out] Retourne un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objet qui représente le résultat de l’évaluation d’expression.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Retourné [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objet contient la valeur de l’expression évaluée. Notez que cette valeur peut être une valeur complexe tel qu’un tableau, mais le résultat final doit être un numérique ou valeur de chaîne qui s’affiche à l’utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

