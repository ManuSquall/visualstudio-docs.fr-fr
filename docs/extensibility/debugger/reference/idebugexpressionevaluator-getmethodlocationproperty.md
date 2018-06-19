---
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f10a26eca06aed24d53b70cd406fe3f24e2fe898
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31111818"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Cette méthode convertit un emplacement de la méthode et le décalage en une adresse mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethodLocationProperty(   
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
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
 [in] Le fournisseur de symbole exprimée sous la forme un [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) objet.  
  
 `pAddress`  
 [in] Une adresse dans la méthode, exprimée sous la forme un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objet.  
  
 `pBinder`  
 [in] Le binder exprimée sous la forme un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objet.  
  
 `ppProperty`  
 [out] Retourne un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface qui représente l’adresse mémoire.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 L’adresse retournée peut être utilisé pour définir un point d’arrêt, par exemple.  
  
 Malgré le nom `upstrFullyQualifiedMethodPlusOffset`, ce paramètre peut être passé à un nom de méthode partiellement qualifié. Dans ce cas, la méthode sélectionnée est celui qui englobe `pAddress`. Interprétation de ce paramètre est l’implémentation de l’évaluateur d’expression et de la langue qu’il prend en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)