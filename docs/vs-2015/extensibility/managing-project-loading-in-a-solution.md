---
title: Gestion du chargement de projet dans une solution | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6598e2f1a178845b3ad2017716576439185379e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839382"
---
# <a name="managing-project-loading-in-a-solution"></a>Gestion du chargement de projet dans une solution
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les solutions Visual Studio peuvent contenir un grand nombre de projets. Le comportement de Visual Studio par défaut consiste à charger tous les projets d’une solution au moment de l’ouverture de la solution, et non à permettre à l’utilisateur d’accéder à tous les projets jusqu’à ce qu’ils aient terminé le chargement. Lorsque le processus de chargement du projet dure plus de deux minutes, une barre de progression s’affiche, affichant le nombre de projets chargés et le nombre total de projets. L’utilisateur peut décharger des projets tout en travaillant dans une solution avec plusieurs projets, mais cette procédure présente quelques inconvénients : les projets déchargés ne sont pas générés dans le cadre d’une commande Rebuild solution, et les descriptions IntelliSense des types et des membres des projets fermés ne sont pas affichées.  
  
 Les développeurs peuvent réduire le temps de chargement de la solution et gérer le comportement de chargement du projet en créant un gestionnaire de chargement de solution. Le gestionnaire de chargement de solution peut définir des priorités de chargement de projet différentes pour des projets ou des types de projets spécifiques, vous assurer que les projets sont chargés avant de démarrer une génération en arrière-plan, retarder le chargement en arrière-plan jusqu’à ce que les autres tâches en arrière-plan soient terminées et effectuer d’autres tâches de gestion  
  
## <a name="project-loading-priorities"></a>Priorités de chargement du projet  
 Visual Studio définit quatre priorités de chargement de projet différentes :  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> (valeur par défaut) : quand une solution est ouverte, les projets sont chargés de façon asynchrone. Si cette priorité est définie sur un projet déchargé une fois que la solution est déjà ouverte, le projet est chargé au point d’inactivité suivant.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: quand une solution est ouverte, les projets sont chargés en arrière-plan, ce qui permet à l’utilisateur d’accéder aux projets à mesure qu’ils sont chargés sans avoir à attendre que tous les projets soient chargés.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: les projets sont chargés lors de leur accès. Un projet est accessible lorsque l’utilisateur développe le nœud de projet dans la Explorateur de solutions, lorsqu’un fichier appartenant au projet est ouvert lorsque la solution s’ouvre, car il se trouve dans la liste des documents ouverts (rendu persistant dans le fichier d’options utilisateur de la solution), ou lorsqu’un autre projet en cours de chargement a une dépendance sur le projet. Ce type de projet n’est pas chargé automatiquement avant le démarrage d’un processus de génération. le gestionnaire de chargement de solution est chargé de s’assurer que tous les projets nécessaires sont chargés. Ces projets doivent également être chargés avant de commencer à rechercher/remplacer dans les fichiers de l’ensemble de la solution.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: les projets ne sont pas chargés à moins que l’utilisateur ne le demande explicitement. C’est le cas lorsque les projets sont déchargés de manière explicite.  
  
## <a name="creating-a-solution-load-manager"></a>Création d’un gestionnaire de chargement de solution  
 Les développeurs peuvent créer un gestionnaire de chargement de solution en implémentant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> et en conseillant à Visual Studio que le gestionnaire de chargement de solution est actif.  
  
#### <a name="activating-a-solution-load-manager"></a>Activation d’un gestionnaire de chargement de solution  
 Visual Studio n’autorise qu’un seul gestionnaire de chargement de solution à un moment donné. vous devez donc conseiller Visual Studio lorsque vous souhaitez activer votre gestionnaire de chargement de solution. Si un deuxième gestionnaire de chargement de solution est activé ultérieurement, votre gestionnaire de chargement de solution sera déconnecté.  
  
 Vous devez récupérer le <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> service et définir la <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propriété :  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Implémentation de IVsSolutionLoadManager  
 La <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> méthode est appelée au cours du processus d’ouverture de la solution. Pour implémenter cette méthode, vous utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> service pour définir la priorité de charge pour le type de projet que vous souhaitez gérer. Par exemple, le code suivant définit les types de projets C# à charger en arrière-plan :  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 La <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> méthode est appelée lors de l’arrêt de Visual Studio ou lorsqu’un package différent est pris en charge par le gestionnaire de chargement de solution actif en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> avec la <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propriété.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Stratégies pour différents types de gestionnaires de chargement de solution  
 Vous pouvez implémenter des gestionnaires de chargement de solution de différentes manières, selon les types de solutions qu’ils sont censés gérer.  
  
 Si le gestionnaire de chargement de solution est destiné à gérer le chargement de solution en général, il peut être implémenté dans le cadre d’un VSPackage. Le package doit être défini sur autoload en ajoutant le <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> sur le VSPackage avec la valeur <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . Le gestionnaire de chargement de solution peut ensuite être activé dans la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode.  
  
> [!NOTE]
> Pour plus d’informations sur le chargement automatique des packages, consultez [chargement des VSPackages](../extensibility/loading-vspackages.md).  
  
 Étant donné que Visual Studio ne reconnaît que le dernier gestionnaire de chargement de solution à activer, les gestionnaires de charge de solution généraux doivent toujours déterminer s’il existe un gestionnaire de chargement avant de l’activer. Si vous appelez GetProperty () sur le service de solution pour les <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> retours `null` , il n’y a aucun gestionnaire de chargement de solution actif. Si elle ne retourne pas de valeur null, vérifiez si l’objet est identique à celui de votre gestionnaire de chargement de solution.  
  
 Si le gestionnaire de chargement de solution est destiné à gérer uniquement quelques types de solution, le VSPackage peut s’abonner aux événements de chargement de solution (en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ) et utiliser le gestionnaire d’événements pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> activer le gestionnaire de chargement de solution.  
  
 Si le gestionnaire de chargement de solution est destiné à gérer uniquement des solutions spécifiques, les informations d’activation peuvent être rendues persistantes dans le cadre du fichier de solution. Pour ce faire, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> pour la section pré-solution.  
  
 Les gestionnaires de chargement de solution spécifiques doivent être désactivés dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> Gestionnaire d’événements, afin de ne pas entrer en conflit avec d’autres gestionnaires de chargement de solution.  
  
 Si vous avez besoin d’un gestionnaire de chargement de solution uniquement pour rendre persistantes les priorités de chargement global du projet (par exemple, les propriétés définies dans une page Options), vous pouvez activer le gestionnaire de chargement de solution dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A> Gestionnaire d’événements, conserver le paramètre dans les propriétés de la solution, puis désactiver le gestionnaire de chargement de solution.  
  
## <a name="handling-solution-load-events"></a>Gestion des événements de chargement de solution  
 Pour vous abonner aux événements de chargement de solution, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> quand vous activez votre gestionnaire de chargement de solution. Si vous implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> , vous pouvez répondre aux événements liés aux différentes priorités de chargement du projet.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Cette est déclenchée avant l’ouverture d’une solution. Vous pouvez l’utiliser pour modifier la priorité de chargement du projet pour les projets de la solution.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Cette opération est déclenchée après le chargement complet de la solution, mais avant le redémarrage du projet en arrière-plan. Par exemple, un utilisateur peut avoir accédé à un projet dont la priorité de charge est LoadIfNeeded, ou le gestionnaire de chargement de la solution a peut-être modifié une priorité de chargement du projet en BackgroundLoad, ce qui démarrerait une charge en arrière-plan de ce projet.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Cette valeur est déclenchée après le chargement initial complet d’une solution, qu’il s’agisse ou non d’un gestionnaire de chargement de solution. Elle est également déclenchée après le chargement en arrière-plan ou la charge de la demande chaque fois que la solution est entièrement chargée. En même temps, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> est réactivé.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Ce est déclenché avant le chargement d’un projet (ou de projets). Pour vous assurer que les autres processus en arrière-plan sont terminés avant le chargement des projets, affectez à la valeur `pfShouldDelayLoadToNextIdle` **true**.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Cette valeur est déclenchée lorsqu’un lot de projets est sur le lieu d’être chargé. Si `fIsBackgroundIdleBatch` a la valeur true, les projets doivent être chargés en arrière-plan ; si `fIsBackgroundIdleBatch` a la valeur false, les projets doivent être chargés de façon synchrone à la suite d’une demande de l’utilisateur, par exemple, si l’utilisateur développe un projet en attente dans Explorateur de solutions. Vous pouvez implémenter cela pour effectuer des tâches coûteuses qui, autrement, auraient besoin d’être effectuées dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Cette commande est déclenchée après le chargement d’un lot de projets.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Détection et gestion du chargement de solutions et de projets  
 Pour détecter l’état de chargement des projets et des solutions, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> avec les valeurs suivantes :  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retourne `true` si la solution et tous ses projets sont chargés ; sinon, `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retourne `true` si un lot de projets est actuellement en cours de chargement en arrière-plan ; sinon, `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retourne `true` si un lot de projets est actuellement chargé en mode synchrone à la suite d’une commande utilisateur ou d’un autre chargement explicite, sinon `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` retourne `true` si la solution est en cours de fermeture ; sinon, `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` retourne `true` si une solution est actuellement ouverte ; sinon, `false` .  
  
  Vous pouvez également vous assurer que les projets et les solutions sont chargés (quelle que soit la priorité de chargement du projet) en appelant l’une des méthodes suivantes :  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: l’appel de cette méthode force le chargement des projets dans une solution avant le retour de la méthode.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: l’appel de cette méthode force le `guidProject` chargement des projets avant le retour de la méthode.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: l’appel de cette méthode force le `guidProjectID` chargement du projet avant le retour de la méthode.  
  
> [!NOTE]
> . Par défaut, seuls les projets qui ont les priorités de chargement à la demande et de chargement en arrière-plan sont chargés, mais si l' <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> indicateur est passé à la méthode, tous les projets sont chargés, à l’exception de ceux qui sont marqués pour être chargés explicitement.
