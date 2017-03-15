---
title: "IDebugExpressionEvaluator::GetMethodProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::GetMethodProperty"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator::GetMethodProperty (méthode)"
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluator::GetMethodProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode extrait un objet de propriété qui contient les variables locales, des arguments, et d'autres propriétés d'une méthode.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetMethodProperty(   
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BOOL                  fIncludeHiddenLocals,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```c#  
int GetMethodProperty(  
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   int                  fIncludeHiddenLocals,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### Paramètres  
 `pSymbolProvider`  
 \[in\]  Le fournisseur de symbole à utiliser, exprimé sous la forme d'un objet d' [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .  
  
 `pAddress`  
 \[in\]  L'adresse dans le code, exprimé sous la forme d'un objet d' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) , qui doit être résolu à la fonction contenant la plus proche.  
  
 `pBinder`  
 \[in\]  Le classeur à utiliser, exprimé sous la forme d'un objet d' [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .  
  
 `fIncludeHiddenLocals`  
 \[in\]  Une valeur différente de zéro \(`TRUE`\) signifie pour inclure les données locales masqués ; un zéro \(d'`FALSE`\) de laisser les données locales masqués  
  
 `ppProperty`  
 \[out\]  Retourne un objet d' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui représente la méthode.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Les variables locales masqués sont en général des variables qui sont générées par le compilateur.  
  
## Voir aussi  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)