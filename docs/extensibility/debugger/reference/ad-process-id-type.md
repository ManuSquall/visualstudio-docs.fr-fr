---
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9df097037a84af9da63f0a98ee6cfa3b28cfcdd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351389"
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
Spécifie comment interpréter un ID de processus dans le [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) structure.

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
ID de processus est un identificateur de système. Utilisez le `ProcessId.dwProcessId` champ la [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) structure.

`AD_PROCESS_ID_GUID`\
ID de processus est un GUID. Utilisez le `ProcessId.guidProcessId` champ la `AD_PROCESS_ID` structure.

## <a name="remarks"></a>Notes
Utilisé pour le `ProcessIdType` membre de la [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) structure pour identifier le type d’ID de processus qui est contenue dans la structure. Détermine comment interpréter le `ProcessId` union dans la structure.

## <a name="requirements"></a>Configuration requise
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
