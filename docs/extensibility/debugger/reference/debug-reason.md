---
title: DEBUG_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8d2ce7eeb28627f7cb0a1dfbe399bd55f04ff7be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921231"
---
# <a name="debug_reason"></a>DEBUG_REASON
Spécifie la raison pour laquelle le processus a été lancé pour le débogage.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>Champs
`DEBUG_REASON_ERROR`\
Une erreur non spécifique s’est produite (il s’agit d’une condition par défaut si aucune des autres raisons ne le tient).

`DEBUG_REASON_USER_LAUNCHED`\
Le processus a été lancé à la demande de l’utilisateur.

`DEBUG_REASON_USER_ATTACHED`\
Le processus déjà en cours d’exécution a été attaché par l’utilisateur.

`DEBUG_REASON_AUTO_ATTACHED`\
Le processus a été automatiquement attaché à lorsqu’il a été lancé.

`DEBUG_REASON_CAUSALITY`\
Le processus a été lancé en raison d’un événement de débogage *juste-à-temps* (JIT).

## <a name="remarks"></a>Remarques
Retourné par la méthode [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) .

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
