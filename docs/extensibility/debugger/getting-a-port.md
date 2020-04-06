---
title: Obtenir un port (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7bf4948e7cb2590136774eab76fbafec91dbfa40
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738630"
---
# <a name="get-a-port"></a>Obtenir un port
Un port représente une connexion à une machine sur laquelle les processus sont en cours d’exécution. Cette machine pourrait être la machine locale ou une machine à distance (qui pourrait éventuellement être en cours d’exécution d’un système d’exploitation non-Windows-basé; voir [Ports](../../extensibility/debugger/ports.md) pour plus d’informations).

Un port est représenté par l’interface [IDebugPort2.](../../extensibility/debugger/reference/idebugport2.md) Il est utilisé pour obtenir des informations sur les processus en cours d’exécution sur la machine à qui le port est connecté.

Un moteur de débogé a besoin d’avoir accès à un port afin d’enregistrer les nœuds de programme avec le port et de satisfaire les demandes d’information sur les processus. Par exemple, si le moteur de débogé implémente [l’interface IDebugProgramProvider2,](../../extensibility/debugger/reference/idebugprogramprovider2.md) la mise en œuvre de la méthode [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) pourrait demander au port que les informations de processus nécessaires soient retournées.

Visual Studio fournit le port nécessaire au moteur de débogé, et il obtient ce port auprès d’un fournisseur de port. Si un programme est attaché à (soit à l’intérieur du débbuggeur ou en raison d’une exception a été jeté, ce qui déclenche la boîte de dialogue Just-in-Time [JIT]), l’utilisateur est donné le choix de transport (un autre nom pour un fournisseur de port) à utiliser. Sinon, si l’utilisateur lance le programme à partir de l’intérieur du débbugger, le système de projet spécifie le fournisseur de port à utiliser. Dans un cas comme dans l’autre, Visual Studio instantanéise le fournisseur de port, représenté par une interface [IDebugPortSupplier2,](../../extensibility/debugger/reference/idebugportsupplier2.md) et demande un nouveau port en appelant [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) avec une interface [IDebugPortRequest2.](../../extensibility/debugger/reference/idebugportrequest2.md) Ce port est ensuite transmis au moteur de débogé sous une forme ou une autre.

## <a name="example"></a>Exemple
Ce fragment de code montre comment utiliser le port fourni à [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) pour enregistrer un nœud de programme dans [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Les paramètres qui ne sont pas directement liés à ce concept ont été omis pour plus de clarté.

> [!NOTE]
> Cet exemple utilise le port pour lancer et reprendre le processus et suppose que l’interface [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) est implémentée sur le port. Ce n’est en aucun cas la seule façon d’effectuer ces tâches, et il est possible que le port ne soit même pas impliqué autre que d’avoir le programme [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) donné à elle.

```cpp
// This is an IDebugEngineLaunch2 method.
HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,
                                      IDebugPort2 *pPort,
                                      /* omitted parameters */,
                                      IDebugProcess2**ppDebugProcess)
{
    // do stuff here to set up for a launch (such as handling the other parameters)
    ...

    // Now get the IPortNotify2 interface so we can register a program node
    // in CDebugEngine::ResumeProcess.
    CComPtr<IDebugDefaultPort2> spDefaultPort;
    HRESULT hr = pPort->QueryInterface(&spDefaultPort);
    if (SUCCEEDED(hr))
    {
        CComPtr<IDebugPortNotify2> spPortNotify;
        hr = spDefaultPort->GetPortNotify(&spPortNotify);
        if (SUCCEEDED(hr))
        {
            // Remember the port notify so we can use it in ResumeProcess.
            m_spPortNotify = spPortNotify;

            // Now launch the process in a suspended state and return the
            // IDebugProcess2 interface
            CComPtr<IDebugPortEx2> spPortEx;
            hr = pPort->QueryInterface(&spPortEx);
            if (SUCCEEDED(hr))
            {
                // pass on the parameters we were given (omitted here)
                hr = spPortEx->LaunchSuspended(/* omitted parameters */,ppDebugProcess)
            }
        }
    }
    return(hr);
}

HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)
{
    // Make a program node for this process
    HRESULT hr;
    CComPtr<IDebugProgramNode2> spProgramNode;
    hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);
    if (SUCCEEDED(hr))
    {
        hr = m_spPortNotify->AddProgramNode(spProgramNode);
        if (SUCCEEDED(hr))
        {
            // resume execution of the process using the port given to us earlier.
            // (Querying for the IDebugPortEx2 interface is valid here since
            // that's how we got the IDebugPortNotify2 interface in the first place.)
            CComPtr<IDebugPortEx2> spPortEx;
            hr = m_spPortNotify->QueryInterface(&spPortEx);
            if (SUCCEEDED(hr))
            {
                hr = spPortEx->ResumeProcess(pDebugProcess);
            }
        }
    }
    return(hr);
}
```

## <a name="see-also"></a>Voir aussi
- [Enregistrement du programme](../../extensibility/debugger/registering-the-program.md)
- [Permettre la déboiffation d’un programme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [Fournisseurs portuaires](../../extensibility/debugger/port-suppliers.md)
- [Ports](../../extensibility/debugger/ports.md)
