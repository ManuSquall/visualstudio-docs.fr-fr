---
title: ATTACH_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca871d9dac2b6f37018af925eece5c1a6f3d1585
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738126"
---
# <a name="attach_reason"></a>ATTACH_REASON
Spécifie la raison pour laquelle le moteur de débogage (DE) doit être attaché à un nœud de programme.

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

## <a name="fields"></a>Champs
`ATTACH_REASON_AUTO`\
Attachement, car le processus est actuellement en mode débogage.

`ATTACH_REASON_LAUNCH`\
Attachement, car le processus a été lancé.

`ATTACH_REASON_USER`\
Attachement en raison d’une demande de l’utilisateur.

## <a name="remarks"></a>Notes
Ces valeurs sont utilisées comme paramètre pour les méthodes d' [attachement](../../../extensibility/debugger/reference/idebugengine2-attach.md) et d' [attachement](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) .

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attacher](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
