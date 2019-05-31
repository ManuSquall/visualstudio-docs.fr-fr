---
title: DEBUG_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0502ab10398d37bcafee5316ba7e7566dbab4e01
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346167"
---
# <a name="debugreason"></a>DEBUG_REASON
Spécifie la raison pour laquelle le processus a été lancé pour le débogage.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>Champs
`DEBUG_REASON_ERROR`\
Une erreur non spécifique s’est produite (utilisé en tant qu’une condition par défaut lorsque aucune des autres raisons ajuster).

`DEBUG_REASON_USER_LAUNCHED`\
Le processus a été lancé à la demande de l’utilisateur.

`DEBUG_REASON_USER_ATTACHED`\
Le processus en cours d’exécution a été attaché à par l’utilisateur.

`DEBUG_REASON_AUTO_ATTACHED`\
Le processus a été automatiquement attaché à lorsqu’elle a été lancée.

`DEBUG_REASON_CAUSALITY`\
Le processus a été lancé en raison un *juste-à-temps* événement de débogage (JIT).

## <a name="remarks"></a>Notes
Retourné par la [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) (méthode).

## <a name="requirements"></a>Configuration requise
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
