---
description: Spécifie les indicateurs du code machine.
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3aeaf00e7073cd1146dcc5856684ed7209e7d800
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170482"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
Spécifie les indicateurs du code machine.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
typedef DWORD DISASSEMBLY_FLAGS;
```

```csharp
public enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
```

## <a name="fields"></a>Champs
`DF_DOCUMENTCHANGE`\
Indique que cette instruction se trouve dans un document différent de celui du précédent.

`DF_DISABLED`\
Indique que cette instruction ne sera pas exécutée.

`DF_INSTRUCTION_ACTIVE`\
Indique que cette instruction est l’une des instructions suivantes à exécuter (il peut y en avoir plusieurs).

`DF_DATA`\
Indique que cette instruction est vraiment des données (et non du code).

`DF_HASSOURCE`\
Indique que cette instruction a une source. Certaines instructions, telles que le profilage ou garbage collection code, n’ont pas de source correspondante.

`DF_DOCUMENT_CHECKSUM`\
Indique que `bstrDocumentUrl` le champ contient des données de somme de contrôle après l’URL du document. Consultez la section Notes de la structure [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) pour savoir comment les données de la somme de contrôle sont stockées.

## <a name="remarks"></a>Notes
Utilisé comme `dwFlags` membre de la structure [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) .

Ces indicateurs peuvent être combinés avec une opération au niveau du bit `OR` .

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
