---
title: IDebugExpressionEvaluator::GetMethodProperty | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords: IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b80507a0ac3406474f26c6e206ac4d69c43ce27c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
  
## <a name="remarks"></a>Remarques  
 Variables locales masqués sont généralement des variables qui sont générés par le compilateur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)