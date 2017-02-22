---
title: "Gestion sp&#233;cialis&#233;e de d&#233;ploiement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "déploiement d'applications (Visual Studio SDK)"
  - "déploiement spécialisée"
ms.assetid: de068b6a-e806-45f0-9dec-2458fbb486f7
caps.latest.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 32
---
# Gestion sp&#233;cialis&#233;e de d&#233;ploiement
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un déploiement est une opération facultative pour les projets.  Un projet Web, par exemple, prend en charge un déploiement pour permettre une mise à jour de projet un serveur Web.  De même, un projet smart device prend en charge un déploiement pour copier une application créée à l'appareil cible.  Sous\-types de projet peuvent fournir le comportement spécialisée de déploiement en implémentant l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .  Cette interface définit un jeu complet des opérations de déploiement :  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.AdviseDeployStatusCallback%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Commit%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStartDeploy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStatusDeploy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Rollback%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StartDeploy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StopDeploy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.UnadviseDeployStatusCallback%2A>  
  
 L'opération réelle de déploiement doit être exécutée dans le thread séparé pour rendre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] encore plus réactive à l'intervention de l'utilisateur.  Les méthodes fournies par <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> sont appelées de façon asynchrone par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et exécutant en arrière\-plan, ce qui permet à l'environnement pour interroger le statut d'une opération de déploiement à tout moment ou pour arrêter l'opération, si nécessaire.  Les opérations de déploiement d'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> sont appelées par l'environnement lorsque l'utilisateur sélectionne la commande deploy.  
  
 Pour informer l'environnement qu'une opération de déploiement a démarré ou s'est terminée, le sous\-type de projet doit appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback.OnStartDeploy%2A> et les méthodes d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback.OnEndDeploy%2A> .  
  
## gérer le déploiement spécialisé  
  
#### pour gérer un déploiement spécialisé par un projet de sous\-type  
  
-   Implémentez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.AdviseDeployStatusCallback%2A> pour stocker l'environnement pour recevoir des notifications d'événements d'état de déploiement.  
  
    ```vb#  
    Private adviseSink As Microsoft.VisualStudio.Shell.EventSinkCollection = New Microsoft.VisualStudio.Shell.EventSinkCollection()  
    Public Function AdviseDeployStatusCallback(ByVal pIVsDeployStatusCallback As IVsDeployStatusCallback, _  
                                               ByRef pdwCookie As UInteger) As Integer  
  
        If pIVsDeployStatusCallback Is Nothing Then  
            Throw New ArgumentNullException("pIVsDeployStatusCallback")  
        End If  
  
        pdwCookie = adviseSink.Add(pIVsDeployStatusCallback)  
        Return VSConstants.S_OK  
  
    End Function  
    ```  
  
    ```c#  
    private Microsoft.VisualStudio.Shell.EventSinkCollection adviseSink = new Microsoft.VisualStudio.Shell.EventSinkCollection();  
    public int AdviseDeployStatusCallback(IVsDeployStatusCallback pIVsDeployStatusCallback,   
                                          out uint pdwCookie)  
    {  
        if (pIVsDeployStatusCallback == null)  
            throw new ArgumentNullException("pIVsDeployStatusCallback");  
  
        pdwCookie = adviseSink.Add(pIVsDeployStatusCallback);  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implémentez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.UnadviseDeployStatusCallback%2A> pour annuler l'inscription de l'environnement pour recevoir des notifications d'événements d'état de déploiement.  
  
    ```vb#  
    Public Function UnadviseDeployStatusCallback(ByVal dwCookie As UInteger) As Integer  
        adviseSink.RemoveAt(dwCookie)  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```c#  
    public int UnadviseDeployStatusCallback(uint dwCookie)  
    {  
        adviseSink.RemoveAt(dwCookie);  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implémentez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Commit%2A> pour effectuer le détail d'opération de validation à votre application.  Cette méthode est utilisée essentiellement pour le déploiement de base de données.  
  
    ```vb#  
    Public Function Commit(ByVal dwReserved As UInteger) As Integer  
        'Implement commit operation here.  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```c#  
    public int Commit(uint dwReserved)  
    {  
         //Implement commit operation here.  
         return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implémentez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Rollback%2A> pour exécuter une opération d'annulation.  Lorsque cette méthode est appelée, le projet de déploiement doit faire tout ce que soit préférable de restaurer des modifications et de restaurer l'état du projet.  Cette méthode est utilisée essentiellement pour le déploiement de base de données.  
  
    ```vb#  
    Public Function Commit(ByVal dwReserved As UInteger) As Integer  
        'Implement commit operation here.  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```c#  
    public int Rollback(uint dwReserved)  
    {  
        //Implement Rollback operation here.  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implémentez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStartDeploy%2A> pour déterminer si un projet peut démarrer une opération de déploiement.  
  
    ```vb#  
    Public Function QueryStartDeploy(ByVal dwOptions As UInteger, ByVal pfSupported As Integer(), ByVal pfReady As Integer()) As Integer  
        If Not pfSupported Is Nothing AndAlso pfSupported.Length > 0 Then  
            pfSupported(0) = 1  
        End If  
        If Not pfReady Is Nothing AndAlso pfReady.Length > 0 Then  
            pfReady(0) = 0  
            If Not deploymentThread Is Nothing AndAlso (Not deploymentThread.IsAlive) Then  
                pfReady(0) = 1  
            End If  
        End If  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```c#  
    public int QueryStartDeploy(uint dwOptions, int[] pfSupported, int[] pfReady)  
    {  
        if (pfSupported != null && pfSupported.Length >0)  
            pfSupported[0] = 1;  
        if (pfReady != null && pfReady.Length >0)  
        {  
            pfReady[0] = 0;  
            if (deploymentThread != null && !deploymentThread.IsAlive)  
                pfReady[0] = 1;  
        }  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implémentez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStatusDeploy%2A> pour déterminer si une opération de déploiement est terminée.  
  
    ```vb#  
    Public Function QueryStatusDeploy(ByRef pfDeployDone As Integer) As Integer  
        pfDeployDone = 1  
        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then  
            pfDeployDone = 0  
        End If  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```c#  
    public int QueryStatusDeploy(out int pfDeployDone)  
    {  
        pfDeployDone = 1;  
        if (deploymentThread != null && deploymentThread.IsAlive)  
            pfDeployDone = 0;  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implémentez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StartDeploy%2A> pour démarrer une opération de déploiement dans un thread séparé.  Placez le code spécifique à votre déploiement de l'application dans la méthode d' `Deploy` .  
  
    ```vb#  
    Public Function StartDeploy(ByVal pIVsOutputWindowPane As IVsOutputWindowPane, ByVal dwOptions As UInteger) As Integer  
        If pIVsOutputWindowPane Is Nothing Then  
            Throw New ArgumentNullException("pIVsOutputWindowPane")  
        End If  
  
        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then  
            Throw New NotSupportedException("Cannot start deployment operation when it is already started; Call QueryStartDeploy first")  
        End If  
  
        outputWindow = pIVsOutputWindowPane  
  
        ' Notify that deployment is about to begin and see if any user wants to cancel.  
        If (Not NotifyStart()) Then  
            Return VSConstants.E_ABORT  
        End If  
  
        operationCanceled = False  
  
        ' Create and start our thread  
        deploymentThread = New Thread(AddressOf Me.Deploy)  
        deploymentThread.Name = "Deployment Thread"  
        deploymentThread.Start()  
  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```c#  
    public int StartDeploy(IVsOutputWindowPane pIVsOutputWindowPane, uint dwOptions)  
    {  
        if (pIVsOutputWindowPane == null)  
            throw new ArgumentNullException("pIVsOutputWindowPane");  
  
        if (deploymentThread != null && deploymentThread.IsAlive)  
            throw new NotSupportedException("Cannot start deployment operation when it is already started; Call QueryStartDeploy first");  
  
        outputWindow = pIVsOutputWindowPane;  
  
        // Notify that deployment is about to begin and see if any user wants to cancel.  
        if (!NotifyStart())  
            return VSConstants.E_ABORT;  
  
        operationCanceled = false;  
  
        // Create and start our thread  
        deploymentThread = new Thread(new ThreadStart(this.Deploy));  
        deploymentThread.Name = "Deployment Thread";  
        deploymentThread.Start();  
  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implémentez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StopDeploy%2A> pour arrêter une opération de déploiement.  Cette méthode est appelée lorsqu'un utilisateur appuie sur le bouton d' **Annuler** pendant le processus de déploiement.  
  
    ```vb#  
    Public Function StopDeploy(ByVal fSync As Integer) As Integer  
        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then  
            Return VSConstants.S_OK  
        End If  
  
        outputWindow.OutputStringThreadSafe("Canceling deployment")  
        operationCanceled = True  
        If fSync <> 0 Then  
            ' Synchronous request, wait for the thread to terminate.  
            If (Not deploymentThread.Join(10000)) Then  
                Debug.Fail("Deployment thread did not terminate before the timeout, Aborting thread")  
                deploymentThread.Abort()  
            End If  
        End If  
  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```c#  
    public int StopDeploy(int fSync)  
    {  
        if (deploymentThread != null && deploymentThread.IsAlive)  
            return VSConstants.S_OK;  
  
        outputWindow.OutputStringThreadSafe("Canceling deployment");  
        operationCanceled = true;  
        if (fSync != 0)  
        {  
            // Synchronous request, wait for the thread to terminate.  
            if (!deploymentThread.Join(10000))  
            {  
                Debug.Fail("Deployment thread did not terminate before the timeout, Aborting thread");  
                deploymentThread.Abort();  
            }  
        }  
  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
> [!NOTE]
>  Tous les exemples de code fournis dans cette rubrique font partie d'un exemple plus complet, [Exemples d’extensibilité Visual Studio](../../misc/vssdk-samples.md).  
  
## Voir aussi  
 [Sous\-types de projets](../../extensibility/internals/project-subtypes.md)