---
title: THREADSTATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50f487b3d44fc1b871b00348ec28693b36c49685
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316141"
---
# <a name="threadstate"></a>THREADSTATE
Spécifie l’état du thread.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
typedef DWORD THREADSTATE;
```

```csharp
public enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
```

## <a name="fields"></a>Champs
 `THREADSTATE_RUNNING`\
 Indique que le thread est en cours d’exécution.

 `THREADSTATE_STOPPED`\
 Indique que le thread est arrêté en raison d’un point d’arrêt.

 `THREADSTATE_FRESH`\
 Indique que le thread a été créé, mais n’exécute pas encore de code.

 `THREADSTATE_DEAD`\
 Indique que le thread est inactif.

 `THREADSTATE_FROZEN`\
 Indique que le thread est figé (aucune exécution ne peut être effectuée).

## <a name="remarks"></a>Notes
 Utilisé pour le `dwThreadState` champ la [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) structure.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)