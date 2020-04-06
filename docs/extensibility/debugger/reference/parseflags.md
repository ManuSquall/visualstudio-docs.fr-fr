---
title: PARSEFLAGS - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0cc70fdd9fe1279e4d419a422b970eb3d3b07c65
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714115"
---
# <a name="parseflags"></a>PARSEFLAGS
Précise comment analyser une expression.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
typedef DWORD PARSEFLAGS;
```

```csharp
public enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
```

## <a name="fields"></a>Champs
 `PARSE_EXPRESSION`\
 Indique que l’expression n’est pas une déclaration.

 `PARSE_FUNCTION_AS_ADDRESS`\
 Indique que l’expression doit être analysée (et évaluée ultérieurement) comme adresse.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 Indique que l’expression est analysée pendant le temps de conception (c’est-à-dire quand un concepteur est ouvert).

## <a name="remarks"></a>Notes
 Passé comme paramètre aux méthodes [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) et [Parse.](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
