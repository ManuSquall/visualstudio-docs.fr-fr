---
title: BP_FLAGS90 Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5628af4a6e5c4deae3de02340e882bd2605e22d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738043"
---
# <a name="bp_flags90"></a>BP_FLAGS90
Énumère les valeurs valides pour les drapeaux optionnels. Les drapeaux optionnels peuvent être utilisés pour spécifier des informations supplémentaires lorsque vous définissez un point d’arrêt. Cette énumération prolonge [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) la BP_FLAGS’énumération.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE               = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION    = 0x0001,
    BP90_FLAG_DONT_STOP          = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
typedef DWORD BP_FLAGS90;
```

```csharp
public enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE                = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION     = 0x0001,
    BP90_FLAG_DONT_STOP           = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
```

## <a name="fields"></a>Champs
`BP90_FLAG_NONE`\
Spécifie aucun drapeau de point d’arrêt.

`BP90_FLAG_MAP_DOCPOSITION`\
Précise que le moteur de débogé (DE) doit cartographier le point d’arrêt en utilisant la position du document. Cela ne s’applique qu’aux points de rupture définis dans les fichiers sources axés sur le script tels que Active Server Pages (ASP).

`BP90_FLAG_DONT_STOP`\
Précise que le point d’arrêt doit être traité par le moteur de débogé, mais que le moteur de débogé ne devrait finalement pas s’arrêter là; c’est-à-dire qu’un objet d’événement [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) ne doit pas être envoyé. Ce drapeau est conçu pour être utilisé principalement avec des points de trace.

`BP90_FLAG_TRACEPOINT_CONTINUE`\
Utilisé par le moteur de débogé indigène pour déterminer si l’état de marche doit être effacé. Il diffère de BP90_FLAG_DONT_STOP parce que BP90_FLAG_DONT_STOP n’est pas réglée si le point de trace exécute une macro.

## <a name="requirements"></a>Spécifications
En-tête: Msdbg90.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
