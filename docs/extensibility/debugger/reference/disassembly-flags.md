---
title: DISASSEMBLY_FLAGS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba6d9db3ad2cb1f9bbc9e3cea27aba939c6dd499
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737372"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
Spécifie les drapeaux pour le démontage.

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
Indique que cette instruction se trouve dans un document différent de celui précédent.

`DF_DISABLED`\
Indique que cette instruction ne sera pas exécutée.

`DF_INSTRUCTION_ACTIVE`\
Indique que cette instruction est l’une des prochaines instructions à exécuter (il peut y en avoir plus d’une).

`DF_DATA`\
Indique que cette instruction est vraiment des données (pas de code).

`DF_HASSOURCE`\
Indique que cette instruction a une source. Certaines instructions, telles que le profilage ou le code de collecte des ordures, n’ont pas de source correspondante.

`DF_DOCUMENT_CHECKSUM`\
Indique `bstrDocumentUrl` que le champ contient des données de checksum après l’URL du document. Consultez la section Remarques pour la structure [de disassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) pour la façon dont les données de checksum sont stockées.

## <a name="remarks"></a>Notes
Utilisé comme `dwFlags` membre de la structure [de démonmblyData.](../../../extensibility/debugger/reference/disassemblydata.md)

Ces drapeaux peuvent être combinés avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
