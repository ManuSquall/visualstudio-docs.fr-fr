---
title: IDebugProgramNode2::Attach_V7 Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdee5b224ae38c3474009aeaf26e783ebc5dd139
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722142"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> Déconseillée. NE PAS UTILISER.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Attach_V7 (
   IDebugProgram2*       pMDMProgram,
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason
);
```

```csharp
int Attach_V7 (
   IDebugProgram2       pMDMProgram,
   IDebugEventCallback2 pCallback,
   uint                 dwReason
);
```

## <a name="parameters"></a>Paramètres

`pMDMProgram`\
[dans] [L’interface IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente le programme à joindre.

`pCallback`\
[dans] [L’interface IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) à utiliser pour envoyer des événements de débog au SDM.

`dwReason`\
[dans] Une valeur de [l’énumération ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) qui spécifie la raison de l’attachement.

## <a name="return-value"></a>Valeur de retour

Une mise en `E_NOTIMPL`œuvre doit toujours revenir .

## <a name="remarks"></a>Notes

> [!WARNING]
> A partir de Visual Studio 2005, cette méthode `E_NOTIMPL`n’est plus utilisée et devrait toujours revenir . Consultez l’interface [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) pour une approche alternative si le nœud du programme doit indiquer `GUID`qu’il ne peut pas être attaché ou si le nœud du programme est tout simplement définir le programme . Sinon, implémenter la méthode [Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="prior-to-visual-studio-2005"></a>Avant Visual Studio 2005

Cette méthode ne doit être mise en œuvre que si le DE s’exécute dans l’espace d’adresse du programme en cours de débocisation. Sinon, cette méthode `S_FALSE`devrait revenir .

Lorsque cette méthode est appelée, le DE doit envoyer l’objet de l’événement [IDebugEngineCreateEvent2,](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) s’il n’a pas déjà été envoyé par exemple de [l’interface IDebugEngine2,](../../../extensibility/debugger/reference/idebugengine2.md) ainsi que les objets de l’événement [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) et [IDebugLoadCompleteEvent2.](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) L’objet de l’événement [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) est ensuite envoyé si le `dwReason` paramètre est `ATTACH_REASON_LAUNCH`.

Le DE doit appeler la méthode [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) sur l’objet [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) fourni par l’objet de l’événement [IDebugProgramCreateEvent2,](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) et doit stocker le GUID de ce programme dans les données de `IDebugProgram2` l’objet mis en œuvre par l’OBJET.

## <a name="see-also"></a>Voir aussi

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
