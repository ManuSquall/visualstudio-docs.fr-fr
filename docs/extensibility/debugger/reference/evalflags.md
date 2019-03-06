---
title: EVALFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d9d59262349891a5c0483297039578c5de4a7b72
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696270"
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

## <a name="members"></a>Membres
EVAL_RETURNVALUE Spécifie que la valeur renvoyée, le cas échéant, être évaluées.

EVAL_NOSIDEEFFECTS Spécifie que des effets secondaires pas.

EVAL_ALLOWBPS Spécifie l’arrêt sur des points d’arrêt.

Spécifie EVAL_ALLOWERRORREPORT rapport d’erreurs à l’hôte pour être autorisée. Principalement utilisé pour l’évaluation de l’expression dans le script dans Internet Explorer.

Fonctions EVAL_FUNCTION_AS_ADDRESS force doit être évaluée en tant qu’adresses, au lieu d’appeler la fonction.

Fonction EVAL_NOFUNCEVAL empêche soit évaluée. Par exemple, considérez le `int` jeton dans l’expression `myExpression(int) + 10`. Cette fonction peut être correctement évaluée en tant qu’adresse, mais pas en tant que valeur.

Indicateur EVAL_NOEVENTS pour indiquer que les événements qui se produisent pendant l’évaluation d’expression ne doivent pas être envoyées pour le Gestionnaire de session de débogage (SDM) ou à l’IDE.

## <a name="remarks"></a>Notes
Ces indicateurs sont passées en tant qu’argument à la [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) et [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) méthodes.

Ces indicateurs peuvent être combinées avec une opération OR au niveau du bit.

## <a name="requirements"></a>Spécifications
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
