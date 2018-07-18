---
title: PROCESS_INFO_FLAGS | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 91e4c4648108cdc6afa28f5a5dd8f9bfd46fcf59
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126345"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS

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

## <a name="members"></a>Membres

PIFLAG_SYSTEM_PROCESS  
Indique que le processus est un processus système.

PIFLAG_DEBUGGER_ATTACHED  
Indique que le processus est en cours de débogage par un débogueur. Il peut être un [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] débogueur, ou il peut être certains autres débogueur, par exemple, le débogueur WinDbg.

PIFLAG_PROCESS_STOPPED  
Indique que le processus est arrêté. Valide uniquement si `PIFLAG_DEBUGGER_ATTACHED` est également spécifié. Disponible dans Visual Studio 2005 et versions ultérieures.

PIFLAG_PROCESS_RUNNING  
Indique que le processus est en cours d’exécution. Valide uniquement si `PIFLAG_DEBUGGER_ATTACHED` est également spécifié. Disponible dans Visual Studio 2005 et versions ultérieures.

## <a name="remarks"></a>Notes

Utilisé pour le `Flags` membre de la [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) structure.

Ces indicateurs peuvent être combinées avec une opération de bits `OR`.

## <a name="requirements"></a>Spécifications

En-tête : msdbg.h

Namespace : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi

[Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)