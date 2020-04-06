---
title: EXCEPTION_STATE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd2e280cd03ae413e0853950d13fbfefb69bc15f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736955"
---
# <a name="exception_state"></a>EXCEPTION_STATE
Spécifie l’état d’exception.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
typedef DWORD EXCEPTION_STATE;
```

```csharp
public enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
```

## <a name="fields"></a>Champs
`EXCEPTION_NONE`\
Ne vous arrêtez pas à l’exception.

`EXCEPTION_STOP_FIRST_CHANCE`\
Arrêtez-vous au premier tir d’exception. Lors de la description d’un événement d’exception, ce drapeau indique que l’événement d’exception est un événement d’exception de première chance.

`EXCEPTION_STOP_SECOND_CHANCE`\
Arrêtez-vous au deuxième tir d’exception. Lorsque vous décrivez un événement d’exception, indique que l’événement d’exception est un événement d’exception de seconde chance.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
Arrêtez-vous au premier tir d’une exception de mode utilisateur. Lorsque vous décrivez un événement d’exception, indique que l’événement d’exception est un événement d’exception utilisateur de première chance.

`EXCEPTION_STOP_USER_UNCAUGHT`\
Arrêtez-vous lorsqu’une exception en mode utilisateur n’est pas détectée. Lors de la description d’un événement d’exception, indique que l’événement d’exception est un événement d’exception en mode utilisateur non prisé.

`EXCEPTION_STOP_ALL`\
Arrêtez-vous à n’importe quelle exception. Non utilisé lors de la description d’un événement d’exception.

`EXCEPTION_CANNOT_BE_CONTINUED`\
Lors de la description d’un événement d’exception, indique que l’exception ne peut pas être poursuivie.

`EXCEPTION_CODE_SUPPORTED`\
Indique que l’exception a le code qui la soutient. Utilisé dans l’affichage d’une exception

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
Indique que le code d’exception doit être affiché dans hexadecimal. Utilisé dans l’affichage d’une exception.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
Indique que le code d’exception prend en charge JustMyCode. Utilisé dans l’affichage d’une exception.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
Indique que le débbuggeur de code géré doit gérer les exceptions. S’il n’est pas défini, le débbuggeur par défaut gère les exceptions. Ceci est transmis à la méthode [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) et n’est pas utilisé dans la structure [EXCEPTION_INFO.](../../../extensibility/debugger/reference/exception-info.md)

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
OBSOLÈTE, NE PAS UTILISER.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
OBSOLÈTE, NE PAS UTILISER.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
OBSOLÈTE, NE PAS UTILISER.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
OBSOLÈTE, NE PAS UTILISER.

## <a name="remarks"></a>Notes
Utilisé comme `dwState` membre de la structure [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) pour indiquer l’état de l’exception et ce qui peut être fait à ce sujet.

Ces valeurs sont également transmises à la méthode [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) pour définir l’état de toutes les exceptions.

Ces drapeaux peuvent être combinés avec un peu plus ou.

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
