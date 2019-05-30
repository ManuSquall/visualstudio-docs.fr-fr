---
title: LAUNCH_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- LAUNCH_FLAGS
helpviewer_keywords:
- LAUNCH_FLAGS enumeration
ms.assetid: f51aab02-d257-4302-bb79-b7d8ba9ac4e5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27975f4055a433891251c675bff3aacaaa9f6bb3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339368"
---
# <a name="launchflags"></a>LAUNCH_FLAGS
Spécifie les indicateurs de lancement du débogage.

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
DÉCONSEILLÉ, N’UTILISEZ PAS.

`LAUNCH_MERGE_ENV`\
Lance le processus et fusionne l’environnement avec l’hôte de lancement.

## <a name="remarks"></a>Notes
Ces valeurs sont passées en tant qu’argument à la [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) (méthode).

Ces indicateurs peuvent être combinées avec un opérateur de bits `OR`.

## <a name="requirements"></a>Configuration requise
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
