---
title: IDebugEngine2::Attach Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93890885dbbdfd3cc26984590955681487977200
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731206"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Attache un moteur de débogé (DE) à un programme ou à des programmes. Appelé par le gestionnaire de déboguer la session (SDM) lorsque le DE est en cours d’exécution dans le processus à la SDM.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Attach( 
   IDebugProgram2**      pProgram,
   IDebugProgramNode2**  rgpProgramNodes,
   DWORD                 celtPrograms,
   IDebugEventCallback2* pCallback,
   ATTACH_REASON         dwReason
);
```

```csharp
int Attach( 
   IDebugProgram2[]     pProgram,
   IDebugProgramNode2[] rgpProgramNodes,
   uint                 celtPrograms,
   IDebugEventCallback2 pCallback,
   Enum_ATTACH_REASON   dwReason
);
```

## <a name="parameters"></a>Paramètres
`pProgram`\
[dans] Une gamme d’objets [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représentent des programmes auxquels il faut s’attacher. Ce sont des programmes portuaires.

`rgpProgramNodes`\
[dans] Une gamme d’objets [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui représentent des nœuds de programme, un pour chaque programme. Les nœuds de programme dans `pProgram`ce tableau représentent les mêmes programmes que dans . Les nœuds du programme sont donnés afin que le DE puisse identifier les programmes auxquels s’attacher.

`celtPrograms`\
[dans] Nombre de programmes et/ou de `pProgram` `rgpProgramNodes` nœuds de programme dans les tableaux et les tableaux.

`pCallback`\
[dans] [L’objet IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) à utiliser pour envoyer des événements de débog au SDM.

`dwReason`\
[dans] Une valeur du [recensement ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) qui précise la raison d’attacher ces programmes. Pour plus d'informations, consultez la section Notes.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Il y a trois raisons de s’attacher à un programme, comme suit :

- `ATTACH_REASON_LAUNCH`indique que le DE s’attache au programme parce que l’utilisateur a lancé le processus qui le contient.

- `ATTACH_REASON_USER`indique que l’utilisateur a explicitement demandé au DE de s’attacher à un programme (ou au processus qui contient un programme).

- `ATTACH_REASON_AUTO`indique que le DE s’attache à un programme particulier parce qu’il déboient déjà d’autres programmes dans un processus particulier. C’est ce qu’on appelle également l’auto-attacher.

  Lorsque cette méthode est appelée, le DE doit envoyer ces événements dans l’ordre:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (s’il n’a pas déjà été envoyé pour un exemple particulier du moteur de débogé)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   En outre, si la raison `ATTACH_REASON_LAUNCH`de l’attachement est , le DE a besoin d’envoyer [l’événement IDebugEntryPointEvent2.](../../../extensibility/debugger/reference/idebugentrypointevent2.md)

   Une fois que le DE obtient [l’objet IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) correspondant au programme étant débogé, il peut être interrogé pour n’importe quelle interface privée.

   Avant d’appeler les méthodes d’un `pProgram` nœud de programme dans le tableau donné par ou `rgpProgramNodes`, l’usurpation d’identité, si nécessaire, doit être activé sur l’interface `IDebugProgram2` qui représente le nœud de programme. Normalement, cependant, cette étape n’est pas nécessaire. Pour plus d’informations, voir [Questions de sécurité](../../../extensibility/debugger/security-issues.md).

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
