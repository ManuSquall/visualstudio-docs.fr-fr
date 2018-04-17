---
title: IDebugExpressionEvaluator::GetMethodProperty | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b5d294e401af09ec3c10fa6dabbb878c661b559e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Cette méthode obtient un objet de propriété qui contient les variables locales, arguments et autres propriétés d’une méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethodProperty(   
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BOOL                  fIncludeHiddenLocals,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodProperty(  
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   int                  fIncludeHiddenLocals,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pSymbolProvider`  
 [in] Le fournisseur de symbole à utiliser, exprimée sous la forme un [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) objet.  
  
 `pAddress`  
 [in] L’adresse dans le code, exprimée sous la forme un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) fonction de l’objet, qui doit être résolue au point le plus proche.  
  
 `pBinder`  
 [in] Le classeur à utiliser, exprimée sous la forme un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objet.  
  
 `fIncludeHiddenLocals`  
 [in] Différent de zéro (`TRUE`) permet d’inclure des variables locales de masqué ; zéro (`FALSE`) revient à omettre les variables locales masqués  
  
 `ppProperty`  
 [out] Retourne un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objet qui représente la méthode.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Variables locales masqués sont généralement des variables qui sont générés par le compilateur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)