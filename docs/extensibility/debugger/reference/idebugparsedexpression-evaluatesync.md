---
description: Cette méthode évalue l’expression analysée et convertit éventuellement le résultat vers un autre type de données.
title: 'IDebugParsedExpression :: EvaluateSync | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75f86506ea3cd29d09bf8c78a07eaabcf7a9a6f0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084634"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Cette méthode évalue l’expression analysée et convertit éventuellement le résultat vers un autre type de données.

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
dans Combinaison de constantes [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) qui contrôlent la manière dont l’expression doit être évaluée.

`dwTimeout`\
dans Spécifie la durée d’attente maximale, en millisecondes, avant le retour de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.

`pSymbolProvider`\
dans Fournisseur de symboles, exprimé sous la forme d’une interface [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .

`pAddress`\
dans Emplacement d’exécution actuel au sein d’une méthode, exprimé sous la forme d’une interface [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`pBinder`\
dans Binder, exprimé sous la forme d’une interface [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .

`bstrResultType`\
dans Type dans lequel le résultat doit être casté. Cet argument peut être une valeur null.

`ppResult`\
à Retourne l’interface [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui représente les résultats de l’évaluation.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Le contexte d’évaluation de l’expression est fourni par `pAddress` , ce qui permet de déterminer la méthode conteneur, puis d’utiliser des règles de portée de langage pour déterminer la valeur des symboles dans l’expression.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
