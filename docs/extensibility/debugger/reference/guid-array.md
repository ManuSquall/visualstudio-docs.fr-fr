---
description: Décrit un tableau d’identificateurs uniques pour les moteurs de débogage disponibles.
title: GUID_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbdc8465bef0795649fef5b169a221a3e7b7178c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162418"
---
# <a name="guid_array"></a>GUID_ARRAY
Décrit un tableau d’identificateurs uniques pour les moteurs de débogage disponibles.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagGUID_ARRAY
{
    DWORD dwCount;
    GUID *Members;
} GUID_ARRAY;
```

```csharp
public struct GUID_ARRAY
{
    public uint dwCount;
    public Guid Members;
}
```

## <a name="members"></a>Membres
`dwCount`\
Nombre d’identificateurs uniques dans le tableau.

`Members`\
Tableau qui contient des identificateurs uniques.

## <a name="remarks"></a>Notes
Cette structure est retournée par la méthode [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md) .

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)
