---
title: PARSEFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56ba1933d1b63f9af863b115972f3ecf1dfc4346
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695711"
---
# <a name="parseflags"></a>PARSEFLAGS
Spécifie comment analyser une expression.

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

## <a name="members"></a>Membres
 PARSE_EXPRESSION indique que l’expression n’est pas une instruction.

 PARSE_FUNCTION_AS_ADDRESS indique que l’expression doit être analysé (et ultérieurement évaluée) en tant qu’adresse.

 PARSE_DESIGN_TIME_EXPR_EVAL indique que l’expression est en cours d’analyse au moment du design (autrement dit, lorsqu’un concepteur est ouvert).

## <a name="remarks"></a>Notes
 Passé en tant que paramètre à la [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) et [analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) méthodes.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)