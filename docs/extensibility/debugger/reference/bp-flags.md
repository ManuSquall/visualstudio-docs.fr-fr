---
description: Fournit des indicateurs facultatifs qui peuvent être utilisés pour spécifier des informations supplémentaires lors de la définition d’un point d’arrêt.
title: BP_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8e35e0b219bb77ce722f2e06a260de7ecc837dfb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085323"
---
# <a name="bp_flags"></a>BP_FLAGS
Fournit des indicateurs facultatifs qui peuvent être utilisés pour spécifier des informations supplémentaires lors de la définition d’un point d’arrêt.

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
Ne spécifie aucun indicateur de point d’arrêt.

`BP_FLAG_MAP_DOCPOSITION`\
Spécifie que le moteur DE débogage (DE) doit mapper le point d’arrêt à l’aide de la position du document. Cela s’applique uniquement aux points d’arrêt définis dans les fichiers sources orientés script tels que les pages de Active Server (ASP).

`BP_FLAG_DONT_STOP`\
Spécifie que le point d’arrêt doit être traité par le moteur de débogage, mais que le moteur de débogage ne doit finalement pas s’arrêter ici (autrement dit, un objet d’événement [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) ne doit pas être envoyé). Cet indicateur est conçu pour être utilisé principalement avec les points de trace.

## <a name="remarks"></a>Notes
Utilisé pour le `dwFlags` membre des structures [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

Ces valeurs peuvent être combinées avec une opération de bits `OR` .

## <a name="requirements"></a>Spécifications
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
