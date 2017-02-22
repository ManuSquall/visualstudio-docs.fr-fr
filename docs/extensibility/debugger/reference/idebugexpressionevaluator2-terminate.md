---
title: "IDebugExpressionEvaluator2::Terminate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Terminer"
  - "IDebugExpressionEvaluator2::Terminate"
ms.assetid: 38265100-4d80-4902-833a-07bb569f9ba8
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionEvaluator2::Terminate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Les points et nettoie l'évaluateur d'expression.  
  
## Syntaxe  
  
```cpp#  
HRESULT Terminate (  
    void  
);  
```  
  
```c#  
int Terminate ();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Indique à l'évaluateur d'expression lorsqu'il est nettoyé.  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet **d'ExpressionEvaluatorPackage** qui expose l'interface d' [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) .  
  
```cpp#  
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
  
## Voir aussi  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)