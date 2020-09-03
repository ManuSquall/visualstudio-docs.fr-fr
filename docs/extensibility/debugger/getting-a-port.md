---
title: Obtention d’un port | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738630"
---
# <a name="get-a-port"></a>Obtenir un port
Un port représente une connexion à un ordinateur sur lequel les processus sont exécutés. Il peut s’agir de l’ordinateur local ou d’un ordinateur distant (qui peut éventuellement exécuter un système d’exploitation non-Windows). pour plus d’informations, consultez [ports](../../extensibility/debugger/ports.md) .

Un port est représenté par l’interface [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) . Il permet d’obtenir des informations sur les processus en cours d’exécution sur la machine à laquelle le port est connecté.

Un moteur de débogage a besoin d’accéder à un port pour inscrire des nœuds de programme auprès du port et satisfaire les demandes d’informations de processus. Par exemple, si le moteur de débogage implémente l’interface [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) , l’implémentation de la méthode [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) peut demander au port de retourner les informations de processus nécessaires.

Visual Studio fournit le port nécessaire au moteur de débogage et obtient ce port à partir d’un fournisseur de port. Si un programme est attaché à (à partir du débogueur ou parce qu’une exception a été levée, ce qui déclenche la boîte de dialogue juste-à-temps [JIT]), l’utilisateur a le choix du transport (un autre nom pour le fournisseur de port) à utiliser. Dans le cas contraire, si l’utilisateur lance le programme à partir du débogueur, le système de projet spécifie le fournisseur de ports à utiliser. Dans les deux cas, Visual Studio instancie le fournisseur de port, représenté par une interface [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , et demande un nouveau port en appelant [addport](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) avec une interface [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) . Ce port est ensuite transmis au moteur de débogage sous une forme ou une autre.

## <a name="example"></a>Exemple
Ce fragment de code montre comment utiliser le port fourni à [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) pour inscrire un nœud de programme dans [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Les paramètres qui ne sont pas directement liés à ce concept ont été omis par souci de clarté.

> [!NOTE]
> Cet exemple utilise le port pour lancer et reprendre le processus et suppose que l’interface [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) est implémentée sur le port. Cela n’est en aucun cas le seul moyen d’effectuer ces tâches, et il est possible que le port ne soit même pas impliqué pour que le [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) du programme soit donné.

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
- [Inscription du programme](../../extensibility/debugger/registering-the-program.md)
- [Activation d’un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [Fournisseurs de port](../../extensibility/debugger/port-suppliers.md)
- [Ports](../../extensibility/debugger/ports.md)
