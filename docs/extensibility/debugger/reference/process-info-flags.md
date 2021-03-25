---
description: Décrit ou spécifie les propriétés d’un processus.
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 66b986fa16f406223c919c6938182b37e1864e98
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079668"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

Décrit ou spécifie les propriétés d’un processus.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
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
Indique que le processus est en cours de débogage par un débogueur. Il peut s’agir d’un [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] débogueur, ou il peut s’agir d’un autre débogueur, par exemple Windbg.

`PIFLAG_PROCESS_STOPPED`\
Indique que le processus est arrêté. Valide uniquement si `PIFLAG_DEBUGGER_ATTACHED` est également spécifié. Disponible dans Visual Studio 2005 et versions ultérieures.

`PIFLAG_PROCESS_RUNNING`\
Indique que le processus est en cours d’exécution. Valide uniquement si `PIFLAG_DEBUGGER_ATTACHED` est également spécifié. Disponible dans Visual Studio 2005 et versions ultérieures.

## <a name="remarks"></a>Notes

Utilisé pour le `Flags` membre de la structure [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) .

Ces indicateurs peuvent être combinés avec une opération au niveau du bit `OR` .

## <a name="requirements"></a>Spécifications

En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi

- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
