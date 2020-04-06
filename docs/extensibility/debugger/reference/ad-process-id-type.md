---
title: AD_PROCESS_ID_TYPE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a88fbe97cede8d343f1a96bc1917a69b8905b02b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738186"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
Précise comment interpréter une pièce d’identité de processus dans la structure [AD_PROCESS_ID.](../../../extensibility/debugger/reference/ad-process-id.md)

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
typedef DWORD AD_PROCESS_ID_TYPE;
```

```csharp
public enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
```

## <a name="fields"></a>Champs
`AD_PROCESS_ID_SYSTEM`\
Process ID est un identifiant système. Utilisez `ProcessId.dwProcessId` le champ de la structure [AD_PROCESS_ID.](../../../extensibility/debugger/reference/ad-process-id.md)

`AD_PROCESS_ID_GUID`\
Process ID est un GUID. Utilisez `ProcessId.guidProcessId` le champ `AD_PROCESS_ID` de la structure.

## <a name="remarks"></a>Notes
Utilisé pour `ProcessIdType` le membre de la structure [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) pour identifier le type d’ID de processus qui est contenu dans la structure. Détermine comment interpréter `ProcessId` le syndicat dans la structure.

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
