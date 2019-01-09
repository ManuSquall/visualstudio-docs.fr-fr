---
title: Démarrage d’une build à partir de l’IDE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- build
ms.assetid: 936317aa-63b7-4eb0-b9db-b260a0306196
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 64d5d9022362b39dea4e9a36155c4c1b3b056c6f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940571"
---
# <a name="start-a-build-from-within-the-ide"></a>Démarrer une build à partir de l’environnement IDE
Les systèmes de projet personnalisés doivent utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildManagerAccessor> pour démarrer des builds. Cet article explique les raisons de cette exigence et décrit la procédure.  

## <a name="parallel-builds-and-threads"></a>Builds et threads parallèles  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] autorise les builds parallèles, ce qui nécessite une médiation pour l’accès aux ressources communes. Les systèmes de projet peuvent exécuter des builds en mode asynchrone, mais ils ne doivent pas appeler de fonctions de génération à partir des rappels qui sont fournis au gestionnaire de build.  

 Si le système de projet modifie des variables d’environnement, il doit définir le NodeAffinity de la build sur OutOfProc. En raison de cette exigence, il n’est pas possible d’utiliser des objets hôtes, puisqu’ils exigent le nœud in-process.  

## <a name="use-ivsbuildmanageraccessor"></a>Utiliser IVSBuildManagerAccessor  
 Le code ci-dessous présente une méthode qui peut être utilisée par un système de projet pour démarrer une build :  

```csharp

public bool Build(Project project, bool isDesignTimeBuild)  
{  
    // Get the accessor from the IServiceProvider interface for the   
    // project system  
    IVsBuildManagerAccessor accessor =  
        serviceProvider.GetService(typeof(SVsBuildManagerAccessor)) as     
        IVsBuildManagerAccessor;  
    bool releaseUIThread = false;  
    try  
    {  
        if(accessor != null)  
        {  
            // Claim the UI thread under the following conditions:  
            // 1. The build must use a resource that uses the UI thread  
            // or,  
            // 2. The build requires the in-proc node AND waits on the   
            // UI thread for the build to complete  
            if(NeedsUIThread)  
            {  
                int result = accessor.ClaimUIThreadForBuild();  
                if(result != S_OK)  
                {  
                     // Not allowed to claim the UI thread right now  
                     return false;  
                }  
                releaseUIThread = true;  
             }  
             if(isDesignTimeBuild)  
             {  
// Start the design time build  
                  int result = accessor.BeginDesignTimeBuild();  
                  if(result != S_OK)  
                  {  
                      // Not allowed to begin a design-time build at  
                      // this time. Try again later.  
                      return false;  
                  }  
             }  
         }  
         bool buildSucceeded = false;  
         // perform project-system specific build set up tasks  
         // Create your BuildRequestData  
         // This assumes a IHostServices variable (hostServices) set   
   // to your host services. If you don't use a project instance   
         // (you build from a file for example) then use another   
         // constructor.  
         BuildRequestData requestData = new   
             BuildRequestData(project.CreateProjectInstance(),   
             "myTarget", hostServices,   
             BuildRequestData.BuildRequestDataFlags.None);  
         // Mark your your submission as Pending  
         BuildSubmission submission =  
              BuildManager.DefaultBuildManager.  
              PendBuildRequest(requestData);  
         // Register the loggers in BuildLoggers  
         if (accessor != null)  
         {  
               foreach (ILogger logger in BuildLoggers)  
               {  
                    accessor.RegisterLogger(submission.SubmissionId,   
                        logger);  
               }  
         }  
         BuildResult buildResult = submission.Execute();  
         return buildResult;  
     }  
     // Clean up resources  
     finally  
     {  
         if(accessor != null)  
         {  
             // Unregister the loggers, if necessary.  
             accessor.UnregisterLoggers(submission.SubmissionId);  
             // Release the UI thread, if used  
             if(releaseUIThread)  
             {  
                  accessor.ReleaseUIThreadForBuild();  
             }  
             // End the design time build, if used  
             if(isDesignTimeBuild)  
             {  
                  accessor.EndDesignTimeBuild();  
             }  
         }  
     }  
}  
```