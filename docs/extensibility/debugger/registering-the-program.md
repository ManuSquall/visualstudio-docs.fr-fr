---
title: Enregistrement du programme (en anglais seulement) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713168"
---
# <a name="register-the-program"></a>Enregistrer le programme
Après l’acquisition d’un port par le moteur de débogé, représenté par une interface [IDebugPort2,](../../extensibility/debugger/reference/idebugport2.md) la prochaine étape pour permettre au programme d’être débogé est de l’enregistrer au port. Une fois inscrit, le programme est disponible pour le débogage par l’un des moyens suivants :

- Le processus d’attachement, qui permet au débogage d’obtenir le contrôle complet de débogage d’une application en cours d’exécution.

- Juste-à-temps (JIT) débogage, qui permet de débogage après le fait d’un programme qui fonctionne indépendamment d’un débbugger. Lorsque l’architecture de temps de fonctionnement attrape un défaut, le débbuggeur est averti avant que le système d’exploitation ou l’environnement de temps d’exécution libère la mémoire et les ressources du programme de défaut.

## <a name="registering-procedure"></a>Procédure d’enregistrement

### <a name="to-register-your-program"></a>Pour enregistrer votre programme

1. Appelez la méthode [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) mise en œuvre par le port.

     `IDebugPortNotify2::AddProgramNode`nécessite un pointeur à une interface [IDebugProgramNode2.](../../extensibility/debugger/reference/idebugprogramnode2.md)

     Habituellement, lorsque le système d’exploitation ou l’environnement de temps d’exécution charge un programme, il crée le nœud de programme. Si le moteur de débogé (DE) est invité à charger le programme, le DE crée et enregistre le nœud du programme.

     L’exemple suivant montre le moteur de débogé de lancer le programme et l’enregistrer avec un port.

    > [!NOTE]
    > Cet échantillon de code n’est pas la seule façon de lancer et de reprendre un processus; ce code est principalement un exemple d’enregistrement d’un programme avec un port.

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
- [Obtenir un port](../../extensibility/debugger/getting-a-port.md)
- [Permettre la déboiffation d’un programme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
