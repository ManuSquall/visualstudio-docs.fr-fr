---
title: LAUNCH_FLAGS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- LAUNCH_FLAGS
helpviewer_keywords:
- LAUNCH_FLAGS enumeration
ms.assetid: f51aab02-d257-4302-bb79-b7d8ba9ac4e5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f18fb850641391f451f5eedb08b7130566dd4de3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714715"
---
# <a name="launch_flags"></a>LAUNCH_FLAGS
Spécifie les drapeaux de lancement de débogé.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_LAUNCH_FLAGS {
    LAUNCH_DEBUG      = 0x0000,
    LAUNCH_NODEBUG    = 0x0001,
    LAUNCH_ENABLE_ENC = 0x0002,
    LAUNCH_MERGE_ENV  = 0x0004
};
typedef DWORD LAUNCH_FLAGS;
```

```csharp
public enum enum_LAUNCH_FLAGS {
    LAUNCH_DEBUG      = 0x0000,
    LAUNCH_NODEBUG    = 0x0001,
    LAUNCH_ENABLE_ENC = 0x0002,
    LAUNCH_MERGE_ENV  = 0x0004
};
```

## <a name="fields"></a>Champs
`LAUNCH_DEBUG`\
Lance le processus de débogage.

`LAUNCH_NODEBUG`\
Lance le processus sans le déboguer.

`LAUNCH_ENABLE_ENC`\
DÉPRÉCIÉS, NE PAS UTILISER.

`LAUNCH_MERGE_ENV`\
Lance le processus et fusionne l’environnement avec l’hôte de lancement.

## <a name="remarks"></a>Notes
Ces valeurs sont transmises comme un argument à la méthode [LaunchSuspended.](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)

Ces drapeaux peuvent être combinés avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
