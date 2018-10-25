---
title: IDebugExpressionEvaluator2::Terminate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Terminate
- IDebugExpressionEvaluator2::Terminate
ms.assetid: 38265100-4d80-4902-833a-07bb569f9ba8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: edc2368edecea28bbe59635b248bb7c0abc7d7a9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929346"
---
# <a name="idebugexpressionevaluator2terminate"></a>IDebugExpressionEvaluator2::Terminate
Arrête et nettoie l’évaluateur d’expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Terminate (  
    void  
);  
```  
  
```csharp  
int Terminate ();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Indique à l’évaluateur d’expression quand il est en cours de nettoyage.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un **ExpressionEvaluatorPackage** objet qui expose le [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) interface.  
  
```cpp  
STDMETHODIMP ExpressionEvaluatorPackage::Terminate(void)  
{  
    // scan the namespaces contained and delete  
    EEExtensionMethodCache **ppChild = NULL;  
    m_HashExtensionMethodCache.ResetHashIterator();  
    while (ppChild = m_HashExtensionMethodCache.IterateHash())  
    {  
        delete *ppChild;  
    }  
    return VBEEImplicitVariables::Terminate();  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)