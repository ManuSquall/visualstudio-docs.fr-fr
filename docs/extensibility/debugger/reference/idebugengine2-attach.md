---
description: Joint un moteur de débogage (DE) à un programme ou à des programmes.
title: 'IDebugEngine2 :: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38275cc623fcb8b30646c9d84ef194f584369ef2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093910"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Joint un moteur de débogage (DE) à un programme ou à des programmes. Appelée par le gestionnaire de débogage de session (SDM) quand le DE est exécuté dans le processus vers le SDM.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Attach( 
   IDebugProgram2**      pProgram,
   IDebugProgramNode2**  rgpProgramNodes,
   DWORD                 celtPrograms,
   IDebugEventCallback2* pCallback,
   ATTACH_REASON         dwReason
);
```

```csharp
int Attach( 
   IDebugProgram2[]     pProgram,
   IDebugProgramNode2[] rgpProgramNodes,
   uint                 celtPrograms,
   IDebugEventCallback2 pCallback,
   Enum_ATTACH_REASON   dwReason
);
```

## <a name="parameters"></a>Paramètres
`pProgram`\
dans Tableau d’objets [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représentent les programmes à attacher. Il s’agit de programmes de port.

`rgpProgramNodes`\
dans Tableau d’objets [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui représentent des nœuds de programme, un pour chaque programme. Les nœuds de programme de ce tableau représentent les mêmes programmes que dans `pProgram` . Les nœuds de programme sont fournis afin que le DE puisse identifier les programmes à attacher.

`celtPrograms`\
dans Nombre de programmes et/ou de nœuds de programme dans les `pProgram` `rgpProgramNodes` tableaux et.

`pCallback`\
dans Objet [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) à utiliser pour envoyer des événements de débogage au SDM.

`dwReason`\
dans Valeur de l’énumération [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) qui spécifie la raison de l’attachement de ces programmes. Pour plus d'informations, consultez la section Notes.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Il existe trois raisons pour attacher un programme, comme suit :

- `ATTACH_REASON_LAUNCH` indique que le DE est attaché au programme, car l’utilisateur a lancé le processus qui le contient.

- `ATTACH_REASON_USER` indique que l’utilisateur a demandé explicitement au DE s’attacher à un programme (ou au processus qui contient un programme).

- `ATTACH_REASON_AUTO` indique que le DE est attaché à un programme particulier, car il débogue déjà d’autres programmes dans un processus particulier. C’est ce que l’on appelle également l’attachement automatique.

  Lorsque cette méthode est appelée, le DE doit envoyer ces événements dans l’ordre :

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (s’il n’a pas déjà été envoyé pour une instance particulière du moteur de débogage)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   En outre, si la raison de l’attachement est `ATTACH_REASON_LAUNCH` , le de doit envoyer l’événement [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) .

   Une fois que le DE obtient l’objet [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) correspondant au programme en cours de débogage, il peut être interrogé pour toute interface privée.

   Avant d’appeler les méthodes d’un nœud de programme dans le tableau donné par `pProgram` ou `rgpProgramNodes` , l’emprunt d’identité, si nécessaire, doit être activé sur l' `IDebugProgram2` interface qui représente le nœud de programme. Toutefois, cette étape n’est généralement pas nécessaire. Pour plus d’informations, consultez [problèmes de sécurité](../../../extensibility/debugger/security-issues.md).

## <a name="see-also"></a>Voir aussi
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
