---
title: "Obtention d&#39;un Port | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ports, mise en route"
  - "débogage (débogage SDK), des ports"
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Obtention d&#39;un Port
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un port représente une connexion à un ordinateur sur lequel les processus.  Cet ordinateur peut être l'ordinateur local ou un ordinateur distant \(qui peut éventuellement effectuer un système d'exploitation non\-Fenêtre\-basé ; consultez [Ports](../../extensibility/debugger/ports.md) pour plus d'informations\).  
  
 un port est représenté par l'interface d' [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) .  Il est utilisé pour obtenir des informations sur les processus en cours de exécution sur l'ordinateur que le port est connecté à.  
  
 Un moteur de débogage a besoin d'accéder à un port pour signaler des nœuds de programme avec le port et répondre à des demandes d'informations de processus.  Par exemple, si le moteur de débogage implémente l'interface d' [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) , l'implémentation de la méthode d' [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) peut demander le port les informations de processus nécessaire être retournée.  
  
 Visual Studio fournit le port nécessaire au moteur de débogage, et il obtient ce port d'un fournisseur de port.  Si un programme est attaché \(du débogueur ou en raison d'une exception a été levée, qui déclenche \[la boîte de dialogue juste\-à\-temps \(JIT\)\], l'utilisateur est fourni le choix de transport \(un autre nom pour un fournisseur de port\) à utiliser.  Sinon, si l'utilisateur lance le programme du débogueur, le système de projet spécifie le fournisseur de port à utiliser.  Dans l'un ou l'autre événement, Visual Studio crée le fournisseur de port, représenté par une interface d' [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , vous demandant un nouveau port en appelant [Ajouter un port](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) avec une interface d' [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) .  Ce port est ensuite passé dans le moteur de débogage sous une forme ou une autre.  
  
## Exemple  
 Ce fragment de code qui montre comment utiliser le port fourni à [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) pour stocker un nœud de programme dans [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md).  Les paramètres pas directement lié à ce concept ont été omis pour plus de clarté.  
  
> [!NOTE]
>  Cet exemple utilise le port pour lancer et reprendre le processus et suppose que l'interface d' [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) est implémentée sur le port.  C'est nullement la seule façon d'effectuer ces tâches, et que le port ne puisse même être impliqué autre que pour avoir [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) du programme donné à celui\-ci.  
  
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
 [Enregistrement du programme](../../extensibility/debugger/registering-the-program.md)   
 [L'activation d'un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Fournisseurs de port](../../extensibility/debugger/port-suppliers.md)   
 [Ports](../../extensibility/debugger/ports.md)