---
description: Cette méthode convertit une chaîne d’expression en expression analysée.
title: IDebugExpressionEvaluator ::P faible | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 560274fa9364e86cbb689af2234f72397f0560fc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092161"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Cette méthode convertit une chaîne d’expression en expression analysée.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Parse( 
   LPCOLESTR                upstrExpression,
   PARSEFLAGS               dwFlags,
   UINT                     nRadix,
   BSTR*                    pbstrError,
   UINT*                    pichError,
   IDebugParsedExpression** ppParsedExpression
);
```

```csharp
int Parse(
   string                     upstrExpression,
   enum_PARSEFLAGS            dwFlags,
   uint                       nRadix,
   out string                 pbstrError,
   out uint                   pichError,
   out IDebugParsedExpression ppParsedExpression
);
```

## <a name="parameters"></a>Paramètres
`upstrExpression`\
dans Chaîne d’expression à analyser.

`dwFlags`\
dans Collection de constantes [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) qui déterminent la façon dont l’expression doit être analysée.

`nRadix`\
dans Base à utiliser pour interpréter toutes les informations numériques.

`pbstrError`\
à Retourne l’erreur sous forme de texte lisible par l’utilisateur.

`pichError`\
à Retourne la position de caractère du début de l’erreur dans la chaîne de l’expression.

`ppParsedExpression`\
à Retourne l’expression analysée dans un objet [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode produit une expression analysée, et non une valeur réelle. Une expression analysée est prête à être évaluée, c’est-à-dire convertie en valeur.

## <a name="see-also"></a>Voir aussi
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
