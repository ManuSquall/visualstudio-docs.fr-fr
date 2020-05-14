---
title: PROCESS_INFO_FLAGS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 36c4cbbe17a109eacd69b76500e8c10d21d2d554
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713961"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

Décrit ou spécifie les propriétés d’un processus.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
```

## <a name="fields"></a>Champs

`PIFLAG_SYSTEM_PROCESS`\
Indique que le processus est un processus système.

`PIFLAG_DEBUGGER_ATTACHED`\
Indique que le processus est déboqué par un débbugger. Il peut [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] être un débbugger, ou il peut être un autre débbugger, par exemple, WinDbg.

`PIFLAG_PROCESS_STOPPED`\
Indique que le processus est arrêté. Valable uniquement `PIFLAG_DEBUGGER_ATTACHED` s’il est également spécifié. Disponible en Visual Studio 2005 et plus tard.

`PIFLAG_PROCESS_RUNNING`\
Indique que le processus est en cours d’exécution. Valable uniquement `PIFLAG_DEBUGGER_ATTACHED` s’il est également spécifié. Disponible en Visual Studio 2005 et plus tard.

## <a name="remarks"></a>Notes

Utilisé pour `Flags` le membre de la structure [PROCESS_INFO.](../../../extensibility/debugger/reference/process-info.md)

Ces drapeaux peuvent être combinés avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications

En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi

- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
