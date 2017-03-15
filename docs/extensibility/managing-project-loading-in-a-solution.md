---
title: "G&#233;rer le chargement de projet dans une Solution | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "solutions de gestion du chargement du projet"
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# G&#233;rer le chargement de projet dans une Solution
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Solutions de Visual Studio peuvent contenir un grand nombre de projets. Le comportement de Visual Studio par défaut consiste à charger tous les projets dans une solution au moment de que l'ouverture de la solution et ne pas pour autoriser l'utilisateur à accéder à tous les projets jusqu'à la fin du chargement de tous les. Lorsque le processus de chargement du projet dure plus de deux minutes, une barre de progression s'affiche, indiquant le nombre de projets chargés et le nombre total de projets. L'utilisateur peut décharger les projets lorsque vous travaillez dans une solution avec plusieurs projets, mais cette procédure présente certains inconvénients : les projets déchargés ne sont pas générés dans le cadre d'une commande Régénérer la Solution, et les descriptions IntelliSense des types et membres de projets clôturés ne sont pas affichés.  
  
 Les développeurs peuvent réduire le temps de chargement de solution et gérer le comportement de chargement en créant une charge de solution responsable de projet. Le Gestionnaire de charge de solution définissez autre projet, le chargement des priorités pour les projets spécifiques ou des types de projet, assurez\-vous que les projets sont chargés avant le démarrage d'une build en arrière\-plan, retarder le chargement d'en arrière\-plan jusqu'à ce que les autres tâches en arrière\-plan sont terminées et effectuer d'autres tâches de gestion de charge de projet.  
  
## Chargement des priorités de projet  
 Visual Studio définit quatre priorités de chargement de projet différent :  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> \(la valeur par défaut\): lorsqu'une solution est ouverte, les projets sont chargées de façon asynchrone. Si cette priorité est définie sur un projet déchargé une fois que la solution est déjà ouverte, le projet sera chargé au prochain point inactif.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: lorsqu'une solution est ouverte, les projets sont chargés en arrière\-plan, permettant à l'utilisateur accéder aux projets chargées sans avoir à attendre jusqu'à ce que tous les projets sont chargés.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: les projets sont chargés lorsqu'ils sont accessibles. Un projet est accessible lorsque l'utilisateur développe le nœud du projet dans l'Explorateur de solutions, lors de l'ouverture d'un fichier appartenant à l'ouverture de la solution, car il se trouve dans la liste des documents ouverts \(persistante dans le fichier d'options utilisateur de la solution\), ou lorsqu'un autre projet qui est en cours de chargement a une dépendance sur le projet. Ce type de projet n'est pas chargé automatiquement avant de démarrer un processus de génération ; le Gestionnaire de charge de Solution est chargé de s'assurer que tous les projets nécessaires sont chargés. Ces projets doivent également être chargés avant de lancer une rechercher\/remplacer dans les fichiers sur toute la solution.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: les projets ne doivent ne pas être chargé, sauf si l'utilisateur le demande explicitement. C'est le cas lorsque les projets sont explicitement déchargés.  
  
## Création d'une charge de solution manager  
 Les développeurs peuvent créer une charge de solution manager en implémentant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> et conseiller Visual Studio que le Gestionnaire de charge de solution est actif.  
  
#### Activation d'un gestionnaire de charge de solution  
 Visual Studio ne permet qu'un seul gestionnaire de charge de solution à un moment donné, donc vous devez informer Visual Studio lorsque vous souhaitez activer la charge de votre solution manager. Si un gestionnaire de charge deuxième solution est activé par la suite, votre gestionnaire de charge solution sera déconnecté.  
  
 Vous devez obtenir le <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> de service et définir le <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propriété :  
  
```c#  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution; object objLoadMgr = this;   //the class that implements IVsSolutionManager pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### L'implémentation de IVsSolutionLoadManager  
 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> méthode est appelée pendant le processus d'ouverture de la solution. Pour implémenter cette méthode, vous utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> service afin de définir la priorité de la charge pour le type de projet que vous souhaitez gérer. Par exemple, le code suivant définit les types de projets c\# pour un chargement en arrière\-plan :  
  
```c#  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}"); pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> méthode est appelée lorsque Visual Studio est en cours d'arrêt ou un autre package a repris en tant que le Gestionnaire de charge de solution active en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> avec la <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propriété.  
  
#### Stratégies pour différents types de gestionnaire de charge de solution  
 Vous pouvez implémenter des gestionnaires de charge de solution de différentes manières, selon les types de solutions qu'elles sont destinées à gérer.  
  
 Si le Gestionnaire de charge de solution est destiné à gérer le chargement en général, il peut être implémenté en tant que partie d'un VSPackage. Le package doit être défini à chargement automatique en ajoutant le <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> sur le VSPackage avec la valeur <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Le Gestionnaire de charge de solution peut ensuite être activé dans le <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> \(méthode\).  
  
> [!NOTE]
>  Pour plus d'informations sur les packages de chargement automatique, consultez [Chargement des packages VS](../extensibility/loading-vspackages.md).  
  
 Depuis Visual Studio reconnaît uniquement le Gestionnaire de charge solution dernière activation, gestionnaires de charge de la solution générale doivent toujours détecter s'il existe un gestionnaire de charge existant avant d'activer eux\-mêmes. Si l'appel GetProperty\(\) sur le service de la solution pour <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> retourne `null`, il n'existe aucun gestionnaire de charge de solution active. Si elle ne retourne pas null, vérifiez si l'objet est le même que votre gestionnaire de charge de solution.  
  
 Si le Gestionnaire de charge de solution est destiné à ne gérer que quelques types de solution, le VSPackage peut s'abonner à des événements de chargement de solution \(en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>\) et utilisez le Gestionnaire d'événements pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> pour activer le Gestionnaire de charge de solution.  
  
 Si le Gestionnaire de charge de solution est destiné à gérer des solutions spécifiques, les informations d'activation peuvent être conservées en tant que partie du fichier solution. Pour ce faire, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> pour la section solution préliminaire.  
  
 Gestionnaires de charge de solution spécifique doivent se désactiver eux\-mêmes dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> Gestionnaire d'événements, afin de ne pas entrer en conflit avec d'autres gestionnaires de charge de solution.  
  
 Si vous avez besoin d'un gestionnaire de charge solution uniquement pour conserver les priorités de charge globale de projet \(par exemple, les propriétés définies sur une page Options\), vous pouvez activer le Gestionnaire de charge de solution dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> Gestionnaire d'événements, conserver le paramètre dans les propriétés de la solution, puis désactiver le Gestionnaire de charge de solution.  
  
## La gestion des événements de chargement de solution  
 Pour vous abonner aux événements de chargement de solution, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> lorsque vous activez le Gestionnaire de charge votre solution. Si vous implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, vous pouvez répondre aux événements qui se rapportent à un autre projet, le chargement des priorités.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Cela est déclenché avant l'ouverture d'une solution. Vous pouvez l'utiliser pour modifier le projet, le chargement de priorité pour les projets dans la solution.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Cela est déclenché après que la solution est entièrement chargée, mais avant l'arrière\-plan du chargement de projet commence à nouveau. Par exemple, un utilisateur a peut\-être accédé un projet dont la priorité de chargement est LoadIfNeeded ou le Gestionnaire de charge de solution peut avoir modifié une priorité de chargement du projet à BackgroundLoad, qui démarre un chargement en arrière\-plan de ce projet.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Déclenché après qu'une solution est entièrement chargée, qu'il existe un gestionnaire de charge de solution ou non. Il est également déclenché après chargement en arrière\-plan ou à la demande de charger chaque fois que la solution est entièrement chargée. En même temps, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> est réactivé.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Elle est déclenchée avant le chargement d'un projet \(ou projets\). Pour vous assurer que les autres processus d'arrière\-plan sont effectuées avant les projets sont chargés, définissez `pfShouldDelayLoadToNextIdle` à **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Elle est déclenchée lorsqu'un lot de projets est sur le point d'être chargé. Si `fIsBackgroundIdleBatch` est true, les projets doivent être chargés en arrière\-plan ; si `fIsBackgroundIdleBatch` a la valeur false, les projets doivent être chargés simultanément à la suite d'une demande de l'utilisateur, par exemple si l'utilisateur développe un projet en attente dans l'Explorateur de solutions. Vous pouvez implémenter ceci pour faire le travail coûteux qui sinon devra être effectuée dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Elle est déclenchée après le chargement d'un lot de projets.  
  
## Détection et la gestion de la solution et le chargement du projet  
 Afin de détecter l'état de chargement de projets et solutions, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> avec les valeurs suivantes :  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retourne `true` Si la solution et tous ses projets sont chargés, sinon `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retourne `true` Si un lot de projets sont actuellement chargés en arrière\-plan, sinon `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retourne `true` Si un lot de projets sont actuellement en cours chargée de façon synchrone en raison d'une commande de l'utilisateur ou autres charge explicite, sinon `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` retourne `true` Si la solution est actuellement en cours de fermeture, sinon `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` retourne `true` Si une solution est actuellement en cours d'ouverture, sinon `false`.  
  
 Vous pouvez également vérifier que les projets et solutions sont chargées \(quels que soient les priorités du projet charge\) en appelant une des méthodes suivantes :  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: cette méthode force les projets dans une solution à charger avant le retour de la méthode.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: cette méthode force les projets `guidProject` chargement avant le retour de la méthode.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: cette méthode force le projet dans `guidProjectID` chargement avant le retour de la méthode.  
  
> [!NOTE]
>  . Par défaut, seuls les projets qui ont la demande chargent et priorités de chargement en arrière\-plan sont chargées, mais si le <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> indicateur est passé à la méthode, à l'exception de celles qui sont marquées pour charger explicitement tous les projets seront chargées.