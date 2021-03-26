---
description: Cette méthode convertit un emplacement et un offset de méthode en une adresse mémoire.
title: 'IDebugExpressionEvaluator :: GetMethodLocationProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ddc9c17b90be6d65786d58ff2bf585461c4fc69f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092187"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Cette méthode convertit un emplacement et un offset de méthode en une adresse mémoire.

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

## <a name="parameters"></a>Paramètres
`upstrFullyQualifiedMethodPlusOffset`\
dans Emplacement et décalage de la méthode, exprimé sous la forme d’une chaîne.

`pSymbolProvider`\
dans Fournisseur de symboles exprimé sous la forme d’un objet [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .

`pAddress`\
dans Adresse dans la méthode, exprimée sous la forme d’un objet [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`pBinder`\
dans Binder exprimé sous la forme d’un objet [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .

`ppProperty`\
à Retourne une interface [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui représente l’adresse mémoire.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 L’adresse retournée peut être utilisée pour définir un point d’arrêt, par exemple.

 Malgré le nom `upstrFullyQualifiedMethodPlusOffset` , un nom de méthode partiellement qualifié peut être passé à ce paramètre. Dans ce cas, la méthode sélectionnée est celle qui est entourée `pAddress` . La façon dont ce paramètre est interprété dépend de l’implémentation de l’évaluateur d’expression et du langage qu’il prend en charge.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
