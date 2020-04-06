---
title: IDebugExpressionEvaluator::GetMethodLocationProperty (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6ba87d6c1a1f7370ce5e209440589f362b87035
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729518"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Cette méthode convertit un emplacement de méthode et compense en une adresse mémoire.

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
[dans] L’emplacement de la méthode et le décalage, exprimé comme une chaîne.

`pSymbolProvider`\
[dans] Le fournisseur de symboles exprimé comme un objet [IDebugSymbolProvider.](../../../extensibility/debugger/reference/idebugsymbolprovider.md)

`pAddress`\
[dans] Une adresse dans la méthode, exprimée comme un objet [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

`pBinder`\
[dans] Le liant exprimé comme un objet [IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)

`ppProperty`\
[out] Retourne une interface [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui représente l’adresse mémoire.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 L’adresse retournée peut être utilisée pour définir un point d’arrêt, par exemple.

 Malgré le `upstrFullyQualifiedMethodPlusOffset`nom, ce paramètre peut être passé un nom de méthode partiellement qualifié. Dans ce cas, la méthode choisie `pAddress`est celle qui s’enferme . La façon dont ce paramètre est interprété est à la mise en œuvre de l’évaluateur d’expression et de la langue qu’il soutient.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
