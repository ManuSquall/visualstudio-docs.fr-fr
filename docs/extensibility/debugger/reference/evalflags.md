---
title: EVALFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2a56f7d5fe4741fa887814691eddcf8df93030cd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337879"
---
# <a name="evalflags"></a>EVALFLAGS
Spécifie les indicateurs qui contrôlent l’évaluation de l’expression.

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
Spécifie que la valeur renvoyée, le cas échéant, être évalué.

`EVAL_NOSIDEEFFECTS`\
Spécifie que les effets secondaires ne seront ne pas autorisées.

`EVAL_ALLOWBPS`\
Spécifie l’arrêt sur des points d’arrêt.

`EVAL_ALLOWERRORREPORT`\
Spécifie le rapport d’erreurs à l’hôte pour être autorisée. Principalement utilisé pour l’évaluation de l’expression dans le script dans Internet Explorer.

`EVAL_FUNCTION_AS_ADDRESS`\
Fonctions de force à évaluer en tant qu’adresses, au lieu d’appeler la fonction.

`EVAL_NOFUNCEVAL`\
Fonction empêche d’en cours d’évaluation. Par exemple, considérez le `int` jeton dans l’expression `myExpression(int) + 10`. Cette fonction peut être correctement évaluée en tant qu’adresse, mais pas en tant que valeur.

`EVAL_NOEVENTS`\
Indicateur pour indiquer que les événements qui se produisent pendant l’évaluation d’expression ne doivent pas être envoyées pour le Gestionnaire de session de débogage (SDM) ou à l’IDE.

## <a name="remarks"></a>Notes
Ces indicateurs sont passées en tant qu’argument à la [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) et [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) méthodes.

Ces indicateurs peuvent être combinées avec une opération OR au niveau du bit.

## <a name="requirements"></a>Configuration requise
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
