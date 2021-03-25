---
description: Spécifie les indicateurs qui contrôlent l’évaluation de l’expression.
title: EVALFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5bcf68b95bb905d41aaab906603cd4dd248e52ad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095938"
---
# <a name="evalflags"></a>EVALFLAGS
Spécifie les indicateurs qui contrôlent l’évaluation de l’expression.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
};
typedef DWORD EVALFLAGS;
```

```csharp
public enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
}
```

## <a name="fields"></a>Champs
`EVAL_RETURNVALUE`\
Spécifie que la valeur de retour, le cas échéant, doit être évaluée.

`EVAL_NOSIDEEFFECTS`\
Spécifie que les effets secondaires ne sont pas autorisés.

`EVAL_ALLOWBPS`\
Spécifie l’arrêt sur les points d’arrêt.

`EVAL_ALLOWERRORREPORT`\
Spécifie les rapports d’erreurs à autoriser pour l’hôte. Principalement utilisé pour l’évaluation de l’expression dans le script dans Internet Explorer.

`EVAL_FUNCTION_AS_ADDRESS`\
Force les fonctions à être évaluées en tant qu’adresses, au lieu d’appeler la fonction.

`EVAL_NOFUNCEVAL`\
Empêche l’évaluation de la fonction. Par exemple, considérez le `int` jeton dans l’expression `myExpression(int) + 10` . Cette fonction peut être correctement évaluée en tant qu’adresse, mais pas en tant que valeur.

`EVAL_NOEVENTS`\
Indicateur qui spécifie que les événements qui se produisent pendant l’évaluation de l’expression ne doivent pas être envoyés au gestionnaire de débogage de session (SDM) ou à l’IDE.

## <a name="remarks"></a>Notes
Ces indicateurs sont passés comme argument aux méthodes [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) et [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) .

Ces indicateurs peuvent être combinés avec une opération or au niveau du bit.

## <a name="requirements"></a>Spécifications
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
