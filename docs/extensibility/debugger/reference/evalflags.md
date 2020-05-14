---
title: EVALFLAGS - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4136726e5c8b798121dbd38975d8f2bb935ed04a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737107"
---
# <a name="evalflags"></a>EVALFLAGS
Spécifie les drapeaux qui contrôlent l’évaluation de l’expression.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_EVALFLAGS {
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
public enum enum_EVALFLAGS {
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
Précise que la valeur de rendement, le cas échéant, doit être évaluée.

`EVAL_NOSIDEEFFECTS`\
Spécifie que les effets secondaires ne sont pas autorisés.

`EVAL_ALLOWBPS`\
Spécifie l’arrêt sur les points d’arrêt.

`EVAL_ALLOWERRORREPORT`\
Spécifie l’autorisation de signaler les erreurs à l’hôte. Principalement utilisé pour l’évaluation de l’expression dans le script dans Internet Explorer.

`EVAL_FUNCTION_AS_ADDRESS`\
Fonctions de forces à évaluer comme adresses, au lieu d’invoquer la fonction.

`EVAL_NOFUNCEVAL`\
Empêche la fonction d’être évaluée. Par exemple, `int` considérez le `myExpression(int) + 10`jeton dans l’expression . Cette fonction peut être correctement évaluée comme une adresse, mais pas comme une valeur.

`EVAL_NOEVENTS`\
Indicateur indiquant que les événements qui se produisent au cours de l’évaluation de l’expression ne doivent pas être envoyés au gestionnaire de débogé de session (SDM) ou à l’IIDE.

## <a name="remarks"></a>Notes
Ces drapeaux sont adoptés comme argument aux méthodes [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) et [EvaluateSync.](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)

Ces drapeaux peuvent être combinés avec un peu plus ou.

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
