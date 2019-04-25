---
title: La gestion du chargement de projet dans une Solution | Microsoft Docs
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
ms.openlocfilehash: cd99d223d8071b4f0c10052b0b42c421d2360e2a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065439"
---
# <a name="managing-project-loading-in-a-solution"></a>Gestion du chargement de projet dans une solution
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Solutions Visual Studio peuvent contenir un grand nombre de projets. Le comportement de Visual Studio par défaut est de charger tous les projets dans une solution au moment de que l’ouverture de la solution et non à autoriser l’utilisateur à accéder à tous les projets jusqu'à la fin du chargement de tous les. Lorsque le processus de chargement de projet dure plus de deux minutes, une barre de progression s’affiche, indiquant le nombre de projets chargés et le nombre total de projets. L’utilisateur peut décharger les projets tout en travaillant dans une solution avec plusieurs projets, mais cette procédure présente certains inconvénients : les projets déchargés ne sont pas générés dans le cadre d’une commande de régénérer la Solution, et les descriptions IntelliSense des types et membres de fermeture projets ne sont pas affichés.  
  
 Les développeurs peuvent réduire les temps de chargement de solution et gérer le comportement de chargement en créant un chargement de solution Gestionnaire de projet. Le Gestionnaire de chargement de solution peut définir l’autre projet, le chargement des priorités pour les projets spécifiques ou des types de projets, assurez-vous que les projets sont chargés avant de démarrer une build en arrière-plan, retarder le chargement d’en arrière-plan jusqu'à ce que les autres tâches en arrière-plan sont terminées et effectuer autres tâches de gestion de charge de projet.  
  
## <a name="project-loading-priorities"></a>Priorités du chargement du projet  
 Visual Studio définit quatre priorités de chargement de projet différent :  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> (la valeur par défaut) : lorsqu’une solution est ouverte, les projets sont chargés de façon asynchrone. Si cette priorité est définie sur un projet déchargé une fois que la solution est déjà ouverte, le projet sera chargé au point inactif suivant.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: lorsqu’une solution est ouverte, les projets sont chargés en arrière-plan, autorisant l’utilisateur à accéder aux projets tels qu’ils sont chargés sans avoir à attendre jusqu'à ce que tous les projets sont chargés.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: les projets sont chargés lorsqu’ils sont accessibles. Un projet est accessible lorsque l’utilisateur développe le nœud du projet dans l’Explorateur de solutions, lorsqu’un fichier appartenant au projet est ouvert lorsque la solution s’ouvre, car il se trouve dans la liste des documents ouverts (persistante dans le fichier d’options utilisateur de la solution), ou lorsqu’un autre projet qui est en cours de chargement a une dépendance sur le projet. Ce type de projet n’est pas chargé automatiquement avant de démarrer un processus de génération ; le Gestionnaire de chargement de Solution est chargé de s’assurer que tous les projets nécessaires sont chargés. Ces projets doivent également être chargés avant de commencer une rechercher/remplacer dans les fichiers sur l’ensemble de la solution.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: les projets ne doivent ne pas être chargé, sauf si l’utilisateur le demande explicitement. C’est le cas lorsque les projets sont déchargés explicitement.  
  
## <a name="creating-a-solution-load-manager"></a>Création d’un chargement de solution manager  
 Les développeurs peuvent créer un chargement de solution manager en implémentant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> et conseiller Visual Studio que le Gestionnaire de chargement de solution est actif.  
  
#### <a name="activating-a-solution-load-manager"></a>Activation d’un gestionnaire de chargement de solution  
 Visual Studio ne permet qu’un seul gestionnaire de chargement de solution à un moment donné, donc vous devez informer Visual Studio lorsque vous souhaitez activer le chargement de votre solution manager. Si un deuxième gestionnaire de chargement de solution est activé par la suite, votre gestionnaire de chargement de solution va être déconnectée.  
  
 Vous devez obtenir le <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> de service et définir le <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propriété :  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Implémentation IVsSolutionLoadManager  
 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> méthode est appelée pendant le processus d’ouverture de la solution. Pour implémenter cette méthode, vous utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> service afin de définir la priorité de chargement pour le type de projet que vous souhaitez gérer. Par exemple, le code suivant définit les types de projets c# pour un chargement en arrière-plan :  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> méthode est appelée lorsque Visual Studio est en cours d’arrêt ou un autre package a repris le dessus comme le Gestionnaire de chargement de solution active en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> avec le <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propriété.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Stratégies pour différents types de gestionnaire de chargement de solution  
 Vous pouvez implémenter des gestionnaires de chargement de solution de différentes manières, selon les types de solutions qu’ils sont destinés à gérer.  
  
 Si le Gestionnaire de chargement de solution est destiné à gérer le chargement en général, elle peut être implémentée en tant que partie d’un VSPackage. Le package doit être défini pour le chargement automatique en ajoutant le <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> sur le VSPackage avec la valeur <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Le Gestionnaire de chargement de solution peut ensuite être activé dans le <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> (méthode).  
  
> [!NOTE]
>  Pour plus d’informations sur les packages de chargement automatique, consultez [le chargement de VSPackages](../extensibility/loading-vspackages.md).  
  
 Dans la mesure où Visual Studio reconnaît uniquement le Gestionnaire de charge solution dernier à être activé, gestionnaires de chargement de solution générale doivent toujours détecter la présence d’un gestionnaire de charge existant avant d’activer eux-mêmes. Si l’appel GetProperty() sur le service de la solution pour <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> retourne `null`, il n’existe aucun gestionnaire de chargement de solution active. Si elle ne retourne pas null, vérifiez si l’objet est le même que le Gestionnaire de charge de votre solution.  
  
 Si le Gestionnaire de chargement de solution est destiné à ne gérer que quelques types de solution, le VSPackage peut s’abonner aux événements de chargement de solution (en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) et utiliser le Gestionnaire d’événements pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> pour activer le Gestionnaire de chargement de solution.  
  
 Si le Gestionnaire de chargement de solution est destiné à gérer des solutions spécifiques, les informations d’activation peuvent être conservées en tant que partie du fichier solution. Pour ce faire, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> pour la section de pré-solution.  
  
 Gestionnaires de chargement de solution spécifique doivent se désactiver eux-mêmes dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> Gestionnaire d’événements, afin de ne pas entrer en conflit avec d’autres gestionnaires de chargement de solution.  
  
 Si vous avez besoin d’un gestionnaire de chargement de solution uniquement pour conserver les priorités de chargement de projets globale (par exemple, les propriétés définies sur une page d’Options), vous pouvez activer le Gestionnaire de chargement de solution dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A> Gestionnaire d’événements, conserver le paramètre dans les propriétés de la solution, puis désactiver le Gestionnaire de chargement de solution.  
  
## <a name="handling-solution-load-events"></a>Gestion des événements de chargement de solution  
 Pour vous abonner aux événements de chargement de solution, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> lorsque vous activez le Gestionnaire de charge de votre solution. Si vous implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, vous pouvez répondre aux événements liés aux priorités de chargement de projet différent.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Elle est déclenchée avant l’ouverture d’une solution. Vous pouvez l’utiliser pour modifier le projet de chargement de priorité pour les projets de la solution.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Elle est déclenchée une fois que la solution est entièrement chargée, mais avant d’arrière-plan le chargement du projet commence à nouveau. Par exemple, un utilisateur a peut-être accédé un projet dont la priorité de chargement est LoadIfNeeded, ou le Gestionnaire de chargement de solution peut avoir changé une priorité de chargement du projet à BackgroundLoad, qui démarre une charge de l’arrière-plan de ce projet.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Elle est déclenchée après qu’une solution est initialement entièrement chargée, s’il existe un gestionnaire de chargement de solution. Il est également déclenché après chargement de l’arrière-plan ou à la demande chargé chaque fois que la solution devienne complètement chargée. En même temps, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> est réactivé.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Elle est déclenchée avant le chargement d’un projet (ou projets). Pour vous assurer que les autres processus d’arrière-plan sont terminées avant que les projets sont chargés, définissez `pfShouldDelayLoadToNextIdle` à **true**.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Elle est déclenchée lorsqu’un lot de projets est sur le point d’être chargé. Si `fIsBackgroundIdleBatch` a la valeur true, les projets doivent être chargés en arrière-plan ; si `fIsBackgroundIdleBatch` a la valeur false, les projets doivent être chargés de façon synchrone à la suite d’une demande d’utilisateur, par exemple si l’utilisateur développe un projet en attente dans l’Explorateur de solutions. Vous pouvez implémenter ceci pour faire le travail coûteux qui sinon devraient être effectuée dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Elle est déclenchée après le chargement d’un lot de projets.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Détection et la gestion de la solution et du chargement de projet  
 Afin de détecter l’état de chargement des projets et solutions, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> avec les valeurs suivantes :  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retourne `true` si la solution et tous ses projets sont chargés, sinon `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retourne `true` si un lot de projets sont actuellement chargés en arrière-plan, sinon `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retourne `true` si un lot de projets sont actuellement en cours chargé de façon synchrone en raison d’une commande de l’utilisateur ou autres chargement explicite, sinon `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` retourne `true` si la solution est actuellement en cours fermée, sinon `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` retourne `true` si une solution est actuellement en cours d’ouverture, sinon `false`.  
  
  Vous pouvez également vous assurer que les projets et solutions sont chargées (quels que soient les priorités de chargement de projet) en appelant une des méthodes suivantes :  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: cette méthode force les projets dans une solution de chargement avant le retour de la méthode.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: cette méthode force les projets de `guidProject` chargement avant le retour de la méthode.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: cette méthode force le projet dans `guidProjectID` chargement avant le retour de la méthode.  
  
> [!NOTE]
>  . Par défaut, seuls les projets qui ont la demande chargent et priorités de chargement en arrière-plan sont chargées, mais si le <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> indicateur est transmis à la méthode, tous les projets seront chargés à l’exception de ceux qui est marqués pour charger explicitement.
