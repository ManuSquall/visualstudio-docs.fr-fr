---
title: IDebugParsedExpression::EvaluateSync Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f00b209ff5f91d160e89f5f55ad966fbe9e6414
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726005"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Cette méthode évalue l’expression analysée et jette le résultat à un autre type de données.

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
[dans] Une combinaison de constantes [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) qui contrôlent la façon dont l’expression doit être évaluée.

`dwTimeout`\
[dans] Spécifie le temps maximum, en millisecondes, d’attendre avant de revenir de cette méthode. Utilisez-le `INFINITE` pour attendre indéfiniment.

`pSymbolProvider`\
[dans] Le fournisseur de symboles, exprimé comme une interface [IDebugSymbolProvider.](../../../extensibility/debugger/reference/idebugsymbolprovider.md)

`pAddress`\
[dans] Le lieu d’exécution actuel dans une méthode, exprimée comme une interface [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

`pBinder`\
[dans] Le liant, exprimé comme une interface [IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)

`bstrResultType`\
[dans] Le type de résultat doit être jeté à. Cet argument peut être une valeur nulle.

`ppResult`\
[out] Retourne l’interface [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui représente les résultats de l’évaluation.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Le contexte d’évaluation `pAddress`de l’expression est donné par , ce qui permet de déterminer la méthode contenante, puis d’utiliser des règles de détermination de la langue pour déterminer la valeur des symboles dans l’expression.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
