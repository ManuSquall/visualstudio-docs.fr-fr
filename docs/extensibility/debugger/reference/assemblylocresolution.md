---
title: ASSEMBLYLOCRESOLUTION ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ASSEMBLYLOCRESOLUTION
helpviewer_keywords:
- ASSEMBLYLOCRESOLUTION enumeration
ms.assetid: 0bcfe85c-5f37-4a9d-bf2b-141acd96ad67
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbd015408cbefd1861f6e795447a5302efabb0dc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738140"
---
# <a name="assemblylocresolution"></a>ASSEMBLYLOCRESOLUTION
Précise où se trouve un assemblage.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_ASSEMBLYLOCRESOLUTION {
    ALR_NAME      = 0x0,
    ALR_USERDIR   = 0x1,
    ALR_SHAREDDIR = 0x2,
    ALR_REMOTEDIR = 0x4,
};
typedef DWORD ASSEMBLYLOCRESOLUTION;
```

```csharp
public enum enum_ASSEMBLYLOCRESOLUTION {
    ALR_NAME      = 0x0,
    ALR_USERDIR   = 0x1,
    ALR_SHAREDDIR = 0x2,
    ALR_REMOTEDIR = 0x4,
};
```

## <a name="fields"></a>Champs
`ALR_NAME`\
L’assemblage est situé dans l’espace nom actuel.

`ALR_USERDIR`\
L’assemblage est situé dans un répertoire d’utilisateurs.

`ALR_SHAREDDIR`\
L’assemblage est situé dans un répertoire partagé.

`ALR_REMOTEDIR`\
L’assemblage est situé dans un répertoire distant.

## <a name="remarks"></a>Notes
Ces valeurs sont retournées par les méthodes [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md) et [GetManagedViewerCreationData.](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)

Ces valeurs peuvent être `OR` combinées avec l’opération.

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)
- [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)
