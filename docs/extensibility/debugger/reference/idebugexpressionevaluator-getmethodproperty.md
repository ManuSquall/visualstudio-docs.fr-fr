---
description: Cette méthode obtient un objet de propriété qui contient les variables locales, les arguments et les autres propriétés d’une méthode.
title: 'IDebugExpressionEvaluator :: GetMethodProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e4a82ce250b47f2f199d9e8e8fcf3a2ca7ec5777
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092174"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Cette méthode obtient un objet de propriété qui contient les variables locales, les arguments et les autres propriétés d’une méthode.

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

## <a name="parameters"></a>Paramètres
`pSymbolProvider`\
dans Fournisseur de symboles à utiliser, exprimé sous la forme d’un objet [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .

`pAddress`\
dans Adresse dans le code, exprimée sous la forme d’un objet [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) , qui doit être résolue à la fonction conteneur la plus proche.

`pBinder`\
dans Binder à utiliser, exprimé sous la forme d’un objet [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .

`fIncludeHiddenLocals`\
dans Une valeur différente `TRUE` de zéro () signifie que les variables locales sont masquées ; zéro ( `FALSE` ) signifie que les variables locales masquées sont ignorées.

`ppProperty`\
à Retourne un objet [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui représente la méthode.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Les variables locales masquées sont généralement des variables générées par le compilateur.

## <a name="see-also"></a>Voir aussi
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
