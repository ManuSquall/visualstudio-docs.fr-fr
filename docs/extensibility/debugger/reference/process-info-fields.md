---
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 835509048e888e13b91c53d9e35bd03d7aebdfed
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56701262"
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
Spécifié le type d’informations à récupérer pour un processus.

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

## <a name="members"></a>Membres
 PIF_FILE_NAME Initialize/utiliser le `bstrFileName` champ la [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) structure.

 PIF_BASE_NAME Initialize/utiliser le `bstrBaseName` champ la `PROCESS_INFO` structure.

 PIF_TITLE Initialize/utiliser le `bstrTitle` champ la `PROCESS_INFO` structure.

 PIF_PROCESS_ID Initialize/utiliser le `ProcessId` champ la `PROCESS_INFO` structure.

 PIF_SESSION_ID Initialize/utiliser le `dwSessionId` champ la `PROCESS_INFO` structure.

 PIF_ATTACHED_SESSION_NAME Initialize/utiliser le `bstrAttachedSessionName` champ la `PROCESS_INFO` structure.

 PIF_CREATION_TIME Initialize/utiliser le `CreationTime` champ la `PROCESS_INFO` structure.

 PIF_FLAGS Initialize/utiliser le `Flags` champ la `PROCESS_INFO` structure.

 PIF_ALL remplit tous les champs.

## <a name="remarks"></a>Notes
 Passé à la [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) méthode pour indiquer les champs de la [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) structure doivent être initialisées.

 Également utilisé dans `Fields` champ la `PROCESS_INFO` structure pour indiquer quels champs sont utilisés et valide.

 Ces indicateurs peuvent être combinées avec un opérateur de bits `OR`.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)