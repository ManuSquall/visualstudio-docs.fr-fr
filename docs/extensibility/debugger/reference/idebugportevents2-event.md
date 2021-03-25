---
description: Cette méthode envoie des événements qui signifient la création et la destruction des processus et des programmes sur un port.
title: 'IDebugPortEvents2 :: Event | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 314c31c426300c31f90813e2b73b150678578437
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058337"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
Cette méthode envoie des événements qui signifient la création et la destruction des processus et des programmes sur un port.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Event(
   IDebugCoreServer2* pServer,
   IDebugPort2*       pPort,
   IDebugProcess2*    pProcess,
   IDebugProgram2*    pProgram,
   IDebugEvent2*      pEvent,
   REFIID             riidEvent
);
```

```csharp
int Event(
   IDebugCoreServer2 pServer,
   IDebugPort2       pPort,
   IDebugProcess2    pProcess,
   IDebugProgram2    pProgram,
   IDebugEvent2      pEvent,
   ref Guid          riidEvent
);
```

## <a name="parameters"></a>Paramètres
`pMachine`\
dans Objet [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) qui représente le serveur de débogage (il existe un pour chaque instance de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ) dans lequel l’événement s’est produit.

`pPort`\
dans Objet [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) qui représente le port dans lequel l’événement s’est produit.

`pProcess`\
dans Objet [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) qui représente le processus dans lequel l’événement s’est produit.

`pProgram`\
dans Objet [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente le programme dans lequel l’événement s’est produit.

`pEvent`\
dans Objet [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) qui identifie l’événement. Les événements possibles sont les suivants :

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
dans GUID de l’événement. Étant donné que l’événement est casté en [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) avant d’appeler cette méthode, cet identificateur facilite la détermination de l’événement qui est envoyé.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
