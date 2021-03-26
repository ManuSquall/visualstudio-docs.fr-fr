---
description: Spécifie comment analyser une expression.
title: PARSEFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7dabef93e8160a2319bc5cefeb189fa335f4b9f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082333"
---
# <a name="parseflags"></a>PARSEFLAGS
Spécifie comment analyser une expression.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
typedef DWORD PARSEFLAGS;
```

```csharp
public enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
```

## <a name="fields"></a>Champs
 `PARSE_EXPRESSION`\
 Indique que l’expression n’est pas une instruction.

 `PARSE_FUNCTION_AS_ADDRESS`\
 Indique que l’expression doit être analysée (et évaluée ultérieurement) en tant qu’adresse.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 Indique que l’expression est analysée au moment de la conception (autrement dit, lorsqu’un concepteur est ouvert).

## <a name="remarks"></a>Notes
 Passé en tant que paramètre aux méthodes [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) et [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) .

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md).
