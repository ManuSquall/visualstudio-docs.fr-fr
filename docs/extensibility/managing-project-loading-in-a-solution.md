---
title: Lors du chargement du projet dans une Solution de gestion | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d0e479a96252710d1f7e6285ffaaa2baf383c061
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146217"
---
# <a name="managing-project-loading-in-a-solution"></a>Lors du chargement de la gestion des projets dans une Solution
Solutions Visual Studio peuvent contenir un grand nombre de projets. Le comportement de Visual Studio par défaut est de chargement de tous les projets dans une solution au moment de que l’ouverture de la solution et ne pas pour autoriser l’utilisateur à accéder aux projets jusqu'à la fin du chargement de tous les. Lorsque le processus de chargement du projet dure plus de deux minutes, une barre de progression affiche le nombre de projets chargés et le nombre total de projets. L’utilisateur peut décharger les projets tout en travaillant dans une solution avec plusieurs projets, mais cette procédure présente certains inconvénients : les projets déchargés ne sont pas générés dans le cadre d’une commande de régénérer la Solution et IntelliSense des descriptions des types et membres de fermeture les projets ne sont pas affichés.  
  
 Les développeurs peuvent réduire les temps de chargement de solutions et gérer le comportement de chargement en créant une charge de solution responsable de projet. Le Gestionnaire de charge de solutions peut vous assurer que les projets sont chargés avant de démarrer une build en arrière-plan, retarder le chargement d’en arrière-plan jusqu'à ce que les autres tâches en arrière-plan sont terminées et effectuer d’autres tâches de gestion de charge de projet.  
  
## <a name="creating-a-solution-load-manager"></a>Création d’une charge de la solution manager  
 Les développeurs peuvent créer une charge de la solution manager en implémentant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> et conseiller Visual Studio que le Gestionnaire de charge de solution est actif.  
  
#### <a name="activating-a-solution-load-manager"></a>Activation d’un gestionnaire de charge de solution  
 Visual Studio ne permet qu’un seul gestionnaire de charge de solution à un moment donné, donc vous devez informer Visual Studio lorsque vous souhaitez activer le chargement de votre solution manager. Si un gestionnaire de charge deuxième solution est activé ultérieurement, le Gestionnaire de charge de votre solution sera déconnecté.  
  
 Vous devez obtenir le <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> de service et de définir le <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propriété :  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> méthode est appelée quand Visual Studio est en cours d’arrêt ou un autre package a repris en tant que le Gestionnaire de charge de solution active en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> avec la <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propriété.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Stratégies pour différents types de gestionnaire de charge de solutions  
 Vous pouvez implémenter des gestionnaires de charge de solutions de différentes façons, selon les types de solutions, qu'ils sont conçus pour gérer.  
  
 Si le Gestionnaire de charge de solutions est destiné à gérer le chargement en général, il peut être implémenté en tant que partie d’un VSPackage. Le package doit être défini sur autoload en ajoutant le <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> sur le VSPackage avec la valeur <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Le Gestionnaire de charge de solutions peut ensuite être activé dans le <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> (méthode).  
  
> [!NOTE]
>  Pour plus d’informations sur les packages chargement automatique, consultez [le chargement des VSPackages](../extensibility/loading-vspackages.md).  
  
 Étant donné que Visual Studio reconnaît uniquement le Gestionnaire de charge solution dernier d’être activées, gestionnaires de charge de solution générale doivent toujours détecter s’il existe un gestionnaire de charge existant avant d’activer eux-mêmes. Si l’appel GetProperty() sur le service de la solution pour <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> retourne `null`, il n’existe aucun gestionnaire de charge de solution active. Si elle ne renvoie pas null, vérifiez si l’objet est le même que le Gestionnaire de charge de votre solution.  
  
 Si le Gestionnaire de charge de solutions est destiné à ne gérer que quelques types de solution, le VSPackage peut s’abonner aux événements de chargement de solution (en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) et utiliser le Gestionnaire d’événements pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> pour activer le Gestionnaire de charge de solutions.  
  
 Si le Gestionnaire de charge de solutions est destiné à gérer des solutions spécifiques, les informations d’activation peuvent être persistante en tant que partie du fichier solution en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> pour la section de solution préliminaire.  
  
 Gestionnaires de charge de solution spécifique doivent se désactiver eux-mêmes dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> Gestionnaire d’événements, pour ne pas entrer en conflit avec d’autres gestionnaires de charge de solution.  
  
 Si vous avez besoin d’un gestionnaire de charge solution uniquement pour conserver les propriétés de projet global charge (par exemple, les propriétés définies sur une page d’Options), vous pouvez activer le Gestionnaire de charge de solutions dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> Gestionnaire d’événements, conserver le paramètre dans les propriétés de la solution, puis désactiver le Gestionnaire de charge de solutions.  
  
## <a name="handling-solution-load-events"></a>La gestion des événements de chargement de solutions  
 Pour vous abonner aux événements de chargement de solution, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> lorsque vous activez le Gestionnaire de charge de votre solution. Si vous implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, vous pouvez répondre aux événements qui se rapportent à un projet différent du chargement des propriétés.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Cet événement est déclenché avant l’ouverture d’une solution.
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Cet événement est déclenché une fois que la solution est entièrement chargée, mais avant d’en arrière-plan le chargement des projets recommence.
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Cet événement est déclenché après le chargement d’une solution entièrement, il existe un gestionnaire de charge de solutions ou non. Il est également déclenché après chargement de l’arrière-plan ou à la demande chargé chaque fois que la solution est entièrement chargée. En même temps, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> est réactivé.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Cet événement est déclenché avant le chargement d’un projet (ou projets). Pour vous assurer que d’autres processus en arrière-plan sont terminées avant que les projets sont chargées, définissez `pfShouldDelayLoadToNextIdle` à **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Cet événement est déclenché lorsqu’un lot de projets est sur le point d’être chargé. Si `fIsBackgroundIdleBatch` a la valeur true, les projets doivent être chargé en arrière-plan ; si `fIsBackgroundIdleBatch` a la valeur false, les projets doivent être chargés de façon synchrone à la suite d’une demande de l’utilisateur, par exemple si l’utilisateur développe un projet en attente dans l’Explorateur de solutions. Vous pouvez gérer cet événement pour exécuter une opération coûteuse qui sinon doit être effectuée dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Cet événement est déclenché après le chargement d’un lot de projets.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Détection et la gestion de la solution et le chargement du projet  
 Afin de détecter l’état de chargement de projets et solutions, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> avec les valeurs suivantes :  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retourne `true` si la solution et tous ses projets sont chargés, sinon `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retourne `true` si un lot de projets est actuellement chargé en arrière-plan, sinon `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retourne `true` si un lot de projets est actuellement en cours chargé de façon synchrone en raison d’une commande de l’utilisateur ou autre charge explicite, sinon `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` retourne `true` si la solution est actuellement en cours fermée, sinon `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` retourne `true` si une solution est actuellement ouvert, dans le cas contraire `false`.  
  
 Vous pouvez également vous assurer que les projets et solutions sont chargées en appelant une des méthodes suivantes :  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: cette méthode force les projets dans une solution à charger avant le retour de la méthode.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: cette méthode force les projets de `guidProject` chargement avant le retour de la méthode.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: cette méthode force le projet dans `guidProjectID` chargement avant le retour de la méthode.  
