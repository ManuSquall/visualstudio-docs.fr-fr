---
title: EVALFLAGS90 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01951885541ba4acce33f3e4f06f7106116ccc62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737100"
---
# <a name="evalflags90"></a>EVALFLAGS90
Énumère les valeurs valides pour les drapeaux qui contrôlent l’évaluation de l’expression. Cette énumération prolonge le recensement [EVALFLAGS.](../../../extensibility/debugger/reference/evalflags.md)

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
Précise que la valeur de rendement, le cas échéant, doit être évaluée.

`EVAL90_NOSIDEEFFECTS`\
Spécifie que les effets secondaires ne sont pas autorisés.

`EVAL90_ALLOWBPS`\
Spécifie l’arrêt sur les points d’arrêt.

`EVAL90_ALLOWERRORREPORT`\
Spécifie que les rapports d’erreur à l’hôte soient autorisés. Principalement utilisé pour l’évaluation de l’expression dans le script dans Internet Explorer.

`EVAL90_FUNCTION_AS_ADDRESS`\
Fonctions de forces à évaluer comme adresses, au lieu d’invoquer la fonction.

`EVAL90_NOFUNCEVAL`\
Empêche la fonction d’être évaluée. Par exemple, `int` considérez le `myExpression(int) + 10`jeton dans l’expression . Cette fonction peut être correctement évaluée comme une adresse, mais pas comme une valeur.

`EVAL90_NOEVENTS`\
Indicateur indiquant que les événements qui se produisent au cours de l’évaluation de l’expression ne doivent pas être envoyés au gestionnaire de débogé de session (SDM) ou à l’IIDE.

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
Permet l’évaluation de l’expression en temps de conception.

`EVAL90_ALLOW_IMPLICIT_VARS`\
Permet la création variable implicite.

`EVAL90_FORCE_EVALUATION_NOW`\
L’évaluation des forces se produira immédiatement. Ceci est utile lors de l’entretien d’une demande, comme une demande d’utilisateur.

## <a name="requirements"></a>Spécifications
En-tête: Msdbg90.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
