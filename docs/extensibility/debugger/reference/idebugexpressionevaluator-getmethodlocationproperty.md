---
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: bdb0598a62de6b16ae8843d61b9346cb86d5cc9e
ms.lasthandoff: 02/22/2017

---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Cette méthode convertit un emplacement de la méthode et le décalage en une adresse mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetMethodLocationProperty(   
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```c#  
int GetMethodLocationProperty(  
   string               upstrFullyQualifiedMethodPlusOffset,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `upstrFullyQualifiedMethodPlusOffset`  
 [in] L’emplacement de la méthode et le décalage, exprimé sous forme de chaîne.  
  
 `pSymbolProvider`  
 [in] Le fournisseur de symboles exprimée sous la forme un [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) objet.  
  
 `pAddress`  
 [in] Une adresse dans la méthode, exprimée comme une [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objet.  
  
 `pBinder`  
 [in] Le binder exprimée sous la forme un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objet.  
  
 `ppProperty`  
 [out] Retourne un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface qui représente l’adresse mémoire.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 L’adresse retournée peut être utilisé pour définir un point d’arrêt, par exemple.  
  
 Malgré son nom `upstrFullyQualifiedMethodPlusOffset`, ce paramètre peut être passé à un nom partiellement qualifié de la méthode. Dans ce cas, la méthode sélectionnée est celui qui englobe `pAddress`. Interprétation de ce paramètre est l’implémentation de l’évaluateur d’expression et le langage que pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
