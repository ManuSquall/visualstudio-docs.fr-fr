---
title: Inscription du programme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b68fa67f784d155288482ad724b632ed5ba5fa41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713168"
---
# <a name="register-the-program"></a>Inscrire le programme
Une fois que le moteur de débogage a acquis un port, représenté par une interface [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , l’étape suivante de l’activation du programme à déboguer consiste à l’inscrire auprès du port. Une fois inscrit, le programme est disponible pour le débogage de l’une des manières suivantes :

- Processus d’attachement, qui permet au débogueur d’obtenir le contrôle complet du débogage d’une application en cours d’exécution.

- Le débogage juste-à-temps (JIT, Just-in-Time), qui permet le débogage d’un programme qui s’exécute indépendamment d’un débogueur. Lorsque l’architecture d’exécution intercepte une erreur, le débogueur est notifié avant que le système d’exploitation ou l’environnement d’exécution ne libère la mémoire et les ressources du programme défaillant.

## <a name="registering-procedure"></a>Procédure d’inscription

### <a name="to-register-your-program"></a>Pour inscrire votre programme

1. Appelez la méthode [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) implémentée par le port.

     `IDebugPortNotify2::AddProgramNode` requiert un pointeur vers une interface [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) .

     En règle générale, lorsque le système d’exploitation ou l’environnement d’exécution charge un programme, il crée le nœud de programme. Si le moteur de débogage (DE) est invité à charger le programme, le DE crée et inscrit le nœud DE programme.

     L’exemple suivant montre le moteur de débogage qui lance le programme et l’enregistre avec un port.

    > [!NOTE]
    > Cet exemple de code n’est pas le seul moyen de lancer et de reprendre un processus. Ce code est principalement un exemple d’inscription d’un programme à l’aide d’un port.

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
                    hr  = spPortEx->ResumeProcess(pDebugProcess);
                }
            }
        }
        return(hr);
    }

    ```

## <a name="see-also"></a>Voir aussi
- [Obtention d’un port](../../extensibility/debugger/getting-a-port.md)
- [Activation d’un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
