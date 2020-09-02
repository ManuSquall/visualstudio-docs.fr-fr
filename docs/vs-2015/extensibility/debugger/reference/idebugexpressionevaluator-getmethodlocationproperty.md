---
title: 'IDebugExpressionEvaluator :: GetMethodLocationProperty | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d82b002d9253b2d48f78e74fdf964cf42d241d9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144393"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode convertit un emplacement et un offset de méthode en une adresse mémoire.  
  
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
 dans Emplacement et décalage de la méthode, exprimé sous la forme d’une chaîne.  
  
 `pSymbolProvider`  
 dans Fournisseur de symboles exprimé sous la forme d’un objet [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .  
  
 `pAddress`  
 dans Adresse dans la méthode, exprimée sous la forme d’un objet [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
 `pBinder`  
 dans Binder exprimé sous la forme d’un objet [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .  
  
 `ppProperty`  
 à Retourne une interface [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui représente l’adresse mémoire.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 L’adresse retournée peut être utilisée pour définir un point d’arrêt, par exemple.  
  
 Malgré le nom `upstrFullyQualifiedMethodPlusOffset` , un nom de méthode partiellement qualifié peut être passé à ce paramètre. Dans ce cas, la méthode sélectionnée est celle qui est entourée `pAddress` . La façon dont ce paramètre est interprété dépend de l’implémentation de l’évaluateur d’expression et du langage qu’il prend en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
