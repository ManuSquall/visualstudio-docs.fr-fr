---
title: PROCESS_INFO_FIELDS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f81709e7146bbdef13daa3564bb784fd9c08d58e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714009"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
Précisez le type d’information à récupérer pour un processus.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
typedef DWORD PROCESS_INFO_FIELDS;
```

```csharp
public enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
```

## <a name="fields"></a>Champs
 `PIF_FILE_NAME`\
 Initialiser/utiliser `bstrFileName` le champ de la structure [PROCESS_INFO.](../../../extensibility/debugger/reference/process-info.md)

 `PIF_BASE_NAME`\
 Initialiser/utiliser `bstrBaseName` le champ `PROCESS_INFO` de la structure.

 `PIF_TITLE`\
 Initialiser/utiliser `bstrTitle` le champ `PROCESS_INFO` de la structure.

 `PIF_PROCESS_ID`\
 Initialiser/utiliser `ProcessId` le champ `PROCESS_INFO` de la structure.

 `PIF_SESSION_ID`\
 Initialiser/utiliser `dwSessionId` le champ `PROCESS_INFO` de la structure.

 `PIF_ATTACHED_SESSION_NAME`\
 Initialiser/utiliser `bstrAttachedSessionName` le champ `PROCESS_INFO` de la structure.

 `PIF_CREATION_TIME`\
 Initialiser/utiliser `CreationTime` le champ `PROCESS_INFO` de la structure.

 `PIF_FLAGS`\
 Initialiser/utiliser `Flags` le champ `PROCESS_INFO` de la structure.

 `PIF_ALL`\
 Remplit tous les champs.

## <a name="remarks"></a>Notes
 Passé à la méthode [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) pour indiquer quels champs de la structure [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) doivent être parasécés.

 Également utilisé `Fields` dans `PROCESS_INFO` le champ de la structure pour indiquer quels champs sont utilisés et valides.

 Ces drapeaux peuvent être combinés avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
