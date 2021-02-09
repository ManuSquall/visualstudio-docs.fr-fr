---
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 451a6ea5334006bb23e8961595f4de85c985b8ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895945"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
Spécifie le type d’informations à récupérer pour un processus.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_PROCESS_INFO_FIELDS { 
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
public enum enum_PROCESS_INFO_FIELDS { 
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
 Initialisez/utilisez le `bstrFileName` champ de la structure [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) .

 `PIF_BASE_NAME`\
 Initialisez/utilisez le `bstrBaseName` champ de la `PROCESS_INFO` structure.

 `PIF_TITLE`\
 Initialisez/utilisez le `bstrTitle` champ de la `PROCESS_INFO` structure.

 `PIF_PROCESS_ID`\
 Initialisez/utilisez le `ProcessId` champ de la `PROCESS_INFO` structure.

 `PIF_SESSION_ID`\
 Initialisez/utilisez le `dwSessionId` champ de la `PROCESS_INFO` structure.

 `PIF_ATTACHED_SESSION_NAME`\
 Initialisez/utilisez le `bstrAttachedSessionName` champ de la `PROCESS_INFO` structure.

 `PIF_CREATION_TIME`\
 Initialisez/utilisez le `CreationTime` champ de la `PROCESS_INFO` structure.

 `PIF_FLAGS`\
 Initialisez/utilisez le `Flags` champ de la `PROCESS_INFO` structure.

 `PIF_ALL`\
 Remplit tous les champs.

## <a name="remarks"></a>Remarques
 Passé à la méthode [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) pour indiquer les champs de la structure [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) qui doivent être initialisés.

 Également utilisé dans `Fields` le champ de la `PROCESS_INFO` structure pour indiquer les champs qui sont utilisés et valides.

 Ces indicateurs peuvent être combinés avec une opération au niveau du bit `OR` .

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
