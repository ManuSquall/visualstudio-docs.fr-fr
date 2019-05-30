---
title: Sources d’événements (Kit de développement logiciel Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], event sources
ms.assetid: b9ba0908-ae4c-4a64-aab1-bee453dd7a22
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96ab4fc69cab50bc5554d626d9c2ac86d49283f4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315309"
---
# <a name="event-sources-visual-studio-sdk"></a>Sources d’événements (SDK Visual Studio)
Il existe deux sources d’événements : le moteur de débogage (dé) et la Session de débogage Manager (SDM). Événements envoyés à partir d’un D’ont un moteur non NULL, tandis que les événements envoyés par le SDM ont un moteur NULL.

## <a name="example"></a>Exemple
L’exemple suivant montre comment envoyer la **IDebugProgramCreateEvent2** à partir de l’Allemagne pour le SDM.

```csharp
CDebugProgramCreateEvent* pProgramCreateEvent = new CDebugProgramCreateEvent();
if (FAILED(pCallback->Event(m_pEngine, NULL, m_pProgram, NULL, pProgramCreateEvent, IID_IDebugProgramCreateEvent2, EVENT_ASYNCHRONOUS)))
{
    // Handle failure here.
}
]

CEvent * pProgCreate = new CEvent(IID_IDebugProgramCreateEvent2, EVENT_ASYNCHRONOUS);
pProgCreate->SendEvent(pCallback, m_pEngine, (IDebugProgram2 *)this, NULL);

HRESULT CEvent::SendEvent(IDebugEventCallback2 *pCallback, IDebugEngine2 *pEngine, IDebugProgram2 *pProgram, IDebugThread2 *pThread) {
    HRESULT hr;

    if (m_dwAttrib & EVENT_STOPPING)
    {
        hr = SendStoppingEvent(pCallback, pEngine, pProgram, pThread);
    }
    else if (m_dwAttrib & EVENT_SYNCHRONOUS)
    {
        hr = SendSynchronousEvent(pCallback, pEngine, pProgram, pThread);
    }
    else
    {
        assert(m_dwAttrib == 0);
        hr = SendAsynchronousEvent(pCallback, pEngine, pProgram, pThread);
    }

    return hr;
}

HRESULT CEvent::SendAsynchronousEvent(IDebugEventCallback2 *pCallback, IDebugEngine2 *pEngine, IDebugProgram2 *pProgram, IDebugThread2 *pThread) {

    HRESULT hr;

    // Make sure the CEvent object running this code is not deleted until the code completes.
    AddRef();

    pCallback->Event(pEngine, NULL, pProgram, pThread, (IDebugEvent2 *)this, m_riid, m_dwAttrib);

    // No error recovery here.
    hr = S_OK;

    Release();
    return hr;
}

```

## <a name="see-also"></a>Voir aussi
- [Envoi d’événements](../../extensibility/debugger/sending-events.md)
