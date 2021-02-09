---
title: 'IDebugProgramNode2 :: Attach_V7 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b143477dc558b20a302a54d5baecc64d02d33ea3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898640"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> Déconseillé. N’UTILISEZ PAS.

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
dans Interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente le programme à attacher.

`pCallback`\
dans Interface [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) à utiliser pour envoyer des événements de débogage au SDM.

`dwReason`\
dans Valeur de l’énumération [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) qui spécifie la raison de l’attachement.

## <a name="return-value"></a>Valeur de retour

Une implémentation doit toujours retourner `E_NOTIMPL` .

## <a name="remarks"></a>Remarques

> [!WARNING]
> À compter de Visual Studio 2005, cette méthode n’est plus utilisée et doit toujours retourner `E_NOTIMPL` . Consultez l’interface [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) pour une autre approche si le nœud de programme doit indiquer qu’il n’est pas possible de l’attacher à ou si le nœud de programme est simplement défini pour le programme `GUID` . Sinon, implémentez la méthode [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .

## <a name="prior-to-visual-studio-2005"></a>Avant Visual Studio 2005

Cette méthode doit être implémentée uniquement si l’DE s’exécute dans l’espace d’adressage du programme en cours de débogage. Sinon, cette méthode doit retourner `S_FALSE` .

Lorsque cette méthode est appelée, le DE doit envoyer l’objet d’événement [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) , s’il n’a pas déjà été envoyé pour cette instance de l’interface [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) , ainsi que les objets d’événement [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) et [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) . L’objet événement [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) est ensuite envoyé si le `dwReason` paramètre est `ATTACH_REASON_LAUNCH` .

Le DE doit appeler la méthode [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) sur l’objet [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) fourni par l’objet d’événement [IDEBUGPROGRAMCREATEEVENT2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) et doit stocker le GUID de ce programme dans les données d’instance pour l' `IDebugProgram2` objet implémenté par l’objet de.

## <a name="see-also"></a>Voir aussi

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
