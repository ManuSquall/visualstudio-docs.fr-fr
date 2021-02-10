---
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72bca5a909b7a001bf12779e54953d403134995b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948411"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
Spécifie comment interpréter un ID de processus dans la structure [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) .

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
L’ID de processus est un identificateur système. Utilisez le `ProcessId.dwProcessId` champ de la structure [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) .

`AD_PROCESS_ID_GUID`\
L’ID de processus est un GUID. Utilisez le `ProcessId.guidProcessId` champ de la `AD_PROCESS_ID` structure.

## <a name="remarks"></a>Notes
Utilisé pour le `ProcessIdType` membre de la structure [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) pour identifier le type d’ID de processus contenu dans la structure. Détermine comment interpréter l' `ProcessId` Union dans la structure.

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
