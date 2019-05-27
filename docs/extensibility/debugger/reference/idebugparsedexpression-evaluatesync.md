---
title: IDebugParsedExpression::EvaluateSync | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1161b97c642b7dc28f2b27037ef3253adf9f6eda
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209734"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Cette méthode évalue l’expression analysée et éventuellement convertit le résultat à un autre type de données.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EvaluateSync( 
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BSTR                  bstrResultType,
   IDebugProperty2**     ppResult
);
```

```csharp
int EvaluateSync(
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   string               bstrResultType,
   out IDebugProperty2  ppResult
);
```

## <a name="parameters"></a>Paramètres
`dwEvalFlags`\
[in] Une combinaison de [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) constantes qui contrôlent la manière dont l’expression doit être évaluée.

`dwTimeout`\
[in] Spécifie la durée maximale, en millisecondes, à attendre avant de retourner à partir de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.

`pSymbolProvider`\
[in] Le fournisseur de symboles, exprimée sous la forme un [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) interface.

`pAddress`\
[in] L’emplacement d’exécution actuel dans une méthode, exprimée sous la forme un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.

`pBinder`\
[in] Le binder, exprimée sous la forme un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface.

`bstrResultType`\
[in] Le type de résultat doit être casté en. Cet argument peut être une valeur null.

`ppResult`\
[out] Retourne le [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface qui représente les résultats d’évaluation.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Le contexte d’évaluation d’expression est fourni par `pAddress`, ce qui rend possible de déterminer la méthode conteneur et utiliser la portée du langage des règles pour déterminer la valeur des symboles dans l’expression.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)