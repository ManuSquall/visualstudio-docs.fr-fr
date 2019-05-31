---
title: AD_PROCESS_ID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID
helpviewer_keywords:
- AD_PROCESS_ID union
ms.assetid: 4cb40d12-2e92-4f09-83f4-689928bd65b3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1893b78063e045f341af246fc0ef2c0f2ad1538e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351411"
---
# <a name="adprocessid"></a>AD_PROCESS_ID
Spécifie l’ID de processus, ce qui peut être un ID système ou un GUID.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _AD_PROCESS_ID {
    AD_PROCESS_ID_TYPE ProcessIdType;
    union {
        DWORD dwProcessId; 
        GUID  guidProcessId; 
        DWORD dwUnused; 
    } ProcessId;
} AD_PROCESS_ID;
```

```csharp
public struct AD_PROCESS_ID {
    AD_PROCESS_ID_TYPE ProcessIdType;
    DWORD              dwProcessId; 
    GUID               guidProcessId; 
    DWORD              dwUnused; 
};
```

## <a name="members"></a>Membres
`ProcessIdType`\
Une valeur comprise entre le [AD_PROCESS_ID_TYPE](../../../extensibility/debugger/reference/ad-process-id-type.md) énumération spécifiant comment interpréter le `ProcessId` union (ou, pour le code managé, le membre de la structure à accéder).

`dwProcessId`\
L’ID de processus en tant que valeur à partir du système.

`guidProcessId`\
L’ID de processus, tel qu’un GUID.

dwUnused Padding.

## <a name="remarks"></a>Notes
Cette structure est passée aux méthodes suivantes :

- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)

- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)

- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)

Et est retournée à partir des méthodes suivantes :

- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

- [GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)

## <a name="requirements"></a>Configuration requise
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
- [AD_PROCESS_ID_TYPE](../../../extensibility/debugger/reference/ad-process-id-type.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
