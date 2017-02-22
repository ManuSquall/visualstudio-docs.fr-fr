---
title: "Enregistrement du programme | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "programmes, l'inscription"
  - "débogage (débogage SDK), programme d'inscription"
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Enregistrement du programme
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Une fois que le moteur de débogage ait acquis un port, représenté par une interface d' [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , l'étape suivante en vérifiant le programme à déboguer est de l'enregistrer avec le port.  Une fois qu'enregistré, le programme est disponible pour déboguer à l'un des moyens suivants :  
  
-   Le processus de s'attacher, qui permet au débogueur au contrôle complet de débogage de gagner d'une application en cours de exécution.  
  
-   Débogage \(JIT\) juste\-à\-temps, qui autorise le débogage d'après\-le\-fait d'un programme qui fonctionne indépendamment d'un débogueur.  Lorsque l'architecture à l'exécution intercepte un défaut, le débogueur est notifié avant le système d'exploitation ou l'environnement d'exécution libère la mémoire et les ressources de la erreur programme.  
  
## Stocker la procédure  
  
#### pour enregistrer votre programme  
  
1.  appelez la méthode d' [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) implémentée par le port.  
  
     `IDebugPortNotify2::AddProgramNode` nécessite un pointeur vers une interface d' [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) .  
  
     En général, lorsque le système d'exploitation ou l'environnement d'exécution charge un programme, elle crée le nœud de programme.  Si le moteur \(DE\) de débogage est pour charger le programme le du crée et enregistre le nœud de programme.  
  
     L'exemple suivant montre le moteur de débogage lancement du programme et l'enregistrement avec un port.  
  
    > [!NOTE]
    >  Ce n'est pas la seule façon de lancer et continuer un processus ; cela constitue principalement un exemple d'inscription d'un programme avec un port.  
  
    ```cpp#  
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
                    hr = spPortEx->LaunchSuspended(/* omitted paramters */,ppDebugProcess)  
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
  
## Voir aussi  
 [Obtention d'un Port](../../extensibility/debugger/getting-a-port.md)   
 [L'activation d'un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)