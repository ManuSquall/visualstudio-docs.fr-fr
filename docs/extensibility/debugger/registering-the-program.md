---
title: Inscription du programme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 873fff0e366f424911db2af4dd9c38a766361c2d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867359"
---
# <a name="register-the-program"></a>Enregistrer le programme
Une fois que le moteur de débogage a acquis un port, représenté par un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interface, l’étape suivante dans le programme à déboguer est pour l’inscrire auprès du port. Une fois inscrit, le programme est disponible pour le débogage par un des moyens suivants :  
  
-   Le processus d’association, ce qui permet au débogueur d’assumer le contrôle de débogage complète d’une application en cours d’exécution.  
  
-   Juste-à-temps (JIT) débogage, ce qui permet de déboguer d’après les faits d’un programme qui s’exécute indépendamment un débogueur. Lors de l’architecture d’exécution intercepte une erreur, le débogueur est notifié avant que le système d’exploitation ou l’environnement d’exécution libère la mémoire et les ressources du programme défaillant.  
  
## <a name="registering-procedure"></a>L’inscription de procédure  
  
### <a name="to-register-your-program"></a>Pour enregistrer votre programme  
  
1.  Appelez le [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) méthode implémentée par le port.  
  
     `IDebugPortNotify2::AddProgramNode` nécessite un pointeur vers un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interface.  
  
     En règle générale, lorsque le système d’exploitation ou un environnement d’exécution charge un programme, il crée le nœud du programme. Si le moteur de débogage (dé) est invité à charger le programme, l’Allemagne crée et enregistre le nœud du programme.  
  
     L’exemple suivant montre le démarrage du programme et en l’inscrivant avec un port du moteur de débogage.  
  
    > [!NOTE]
    >  Cet exemple de code n’est pas le seul moyen de lancer et de reprendre un processus ; Ce code est principalement un exemple d’inscription d’un programme avec un port.  
  
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
 [Obtention d’un port](../../extensibility/debugger/getting-a-port.md)   
 [Activation d’un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)