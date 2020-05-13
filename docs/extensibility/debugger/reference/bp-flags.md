---
title: BP_FLAGS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62626ff75a4545d89835d3136649191004291f8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738064"
---
# <a name="bp_flags"></a>BP_FLAGS
Fournit des drapeaux optionnels qui peuvent être utilisés pour spécifier des informations supplémentaires lors de la configuration d’un point d’arrêt.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
typedef DWORD BP_FLAGS;
```

```csharp
public enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
```

## <a name="fields"></a>Champs
`BP_FLAG_NONE`\
Spécifie aucun drapeau de point d’arrêt.

`BP_FLAG_MAP_DOCPOSITION`\
Précise que le moteur de débogé (DE) doit cartographier le point d’arrêt à l’aide de la position du document. Cela ne s’applique qu’aux points de rupture définis dans les fichiers sources axés sur le script tels que Active Server Pages (ASP).

`BP_FLAG_DONT_STOP`\
Précise que le point d’arrêt doit être traité par le moteur de débogé, mais que le moteur de débogé ne devrait finalement pas s’arrêter là (c’est-à-dire qu’un objet d’événement [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) ne doit pas être envoyé). Ce drapeau est conçu pour être utilisé principalement avec des points de trace.

## <a name="remarks"></a>Notes
Utilisé pour `dwFlags` le membre des structures [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

Ces valeurs peuvent être combinées avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
