---
description: Énumère les valeurs valides pour les indicateurs qui contrôlent l’évaluation de l’expression.
title: EVALFLAGS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2080eba4b8319045dcd4d3603d1e6441fafed97d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150924"
---
# <a name="evalflags90"></a>EVALFLAGS90
Énumère les valeurs valides pour les indicateurs qui contrôlent l’évaluation de l’expression. Cette énumération étend l’énumération [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) .

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
typedef DWORD EVALFLAGS90;
```

```csharp
public enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
```

## <a name="fields"></a>Champs
`EVAL90_RETURNVALUE`\
Spécifie que la valeur de retour, le cas échéant, doit être évaluée.

`EVAL90_NOSIDEEFFECTS`\
Spécifie que les effets secondaires ne sont pas autorisés.

`EVAL90_ALLOWBPS`\
Spécifie l’arrêt sur les points d’arrêt.

`EVAL90_ALLOWERRORREPORT`\
Spécifie que le rapport d’erreurs à l’hôte doit être autorisé. Principalement utilisé pour l’évaluation de l’expression dans le script dans Internet Explorer.

`EVAL90_FUNCTION_AS_ADDRESS`\
Force les fonctions à être évaluées en tant qu’adresses, au lieu d’appeler la fonction.

`EVAL90_NOFUNCEVAL`\
Empêche l’évaluation de la fonction. Par exemple, considérez le `int` jeton dans l’expression `myExpression(int) + 10` . Cette fonction peut être correctement évaluée en tant qu’adresse, mais pas en tant que valeur.

`EVAL90_NOEVENTS`\
Indicateur qui spécifie que les événements qui se produisent pendant l’évaluation de l’expression ne doivent pas être envoyés au gestionnaire de débogage de session (SDM) ou à l’IDE.

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
Active l’évaluation d’une expression au moment du Design.

`EVAL90_ALLOW_IMPLICIT_VARS`\
Autorise la création de variables implicites.

`EVAL90_FORCE_EVALUATION_NOW`\
Force l’évaluation à se produire immédiatement. Cela est utile lors de la maintenance d’une demande, par exemple une demande de l’utilisateur.

## <a name="requirements"></a>Configuration requise
En-tête : Msdbg90. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
