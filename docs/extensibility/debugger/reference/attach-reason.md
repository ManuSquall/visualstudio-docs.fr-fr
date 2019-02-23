---
title: ATTACH_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11fba0944ca1b23c22caae6f0d6a4d9455099946
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688262"
---
# <a name="attachreason"></a>ATTACH_REASON
Spécifie la raison pour le moteur de débogage (dé) à attacher à un nœud de programme.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
typedef DWORD ATTACH_REASON;
```

```csharp
public enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
```

## <a name="members"></a>Membres
ATTACH_REASON_AUTO attacher, car le processus est actuellement en mode débogage.

ATTACH_REASON_LAUNCH attacher, car le processus a été lancé.

ATTACH_REASON_USER joindre en raison d’une demande de l’utilisateur.

## <a name="remarks"></a>Notes
Ces valeurs sont utilisées en tant que paramètre à la [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) et [attacher](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) méthodes.

## <a name="requirements"></a>Spécifications
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attacher](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
