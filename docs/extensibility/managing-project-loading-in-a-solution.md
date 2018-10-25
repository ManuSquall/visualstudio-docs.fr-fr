---
title: La gestion du chargement de projet dans une Solution | Microsoft Docs
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
ms.openlocfilehash: 2ead4834f1d29baff099eedbf464c1ba6344ca6c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950197"
---
# <a name="manage-project-loading-in-a-solution"></a>Gérer le chargement du projet dans une solution
Solutions Visual Studio peuvent contenir un grand nombre de projets. Le comportement de Visual Studio par défaut est de charger tous les projets dans une solution au moment de que l’ouverture de la solution et non à autoriser l’utilisateur à accéder à tous les projets jusqu'à la fin du chargement de tous les. Lorsque le processus de chargement de projet dure plus de deux minutes, une barre de progression s’affiche, indiquant le nombre de projets chargés et le nombre total de projets. L’utilisateur peut décharger les projets tout en travaillant dans une solution avec plusieurs projets, mais cette procédure présente certains inconvénients : les projets déchargés ne sont pas générés dans le cadre d’une commande de régénérer la Solution, et les descriptions IntelliSense des types et membres de fermeture projets ne sont pas affichés.  
  
 Les développeurs peuvent réduire les temps de chargement de solution et gérer le comportement de chargement en créant un chargement de solution Gestionnaire de projet. Le Gestionnaire de chargement de solution peut vous assurer que les projets sont chargés avant de démarrer une build en arrière-plan, retarder le chargement d’en arrière-plan jusqu'à ce que les autres tâches en arrière-plan sont terminées et effectuer d’autres tâches de gestion de charge de projet.  
  
## <a name="create-a-solution-load-manager"></a>Créer un chargement de solution manager  
 Les développeurs peuvent créer un chargement de solution manager en implémentant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> et conseiller Visual Studio que le Gestionnaire de chargement de solution est actif.  
  
### <a name="activate-a-solution-load-manager"></a>Activer un gestionnaire de chargement de solution  
 Visual Studio ne permet qu’un seul gestionnaire de chargement de solution à un moment donné, donc vous devez informer Visual Studio lorsque vous souhaitez activer le chargement de votre solution manager. Si un deuxième gestionnaire de chargement de solution est activé par la suite, votre gestionnaire de chargement de solution va être déconnectée.  
  
 Vous devez obtenir le <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> de service et définir le <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propriété :  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> méthode est appelée lorsque Visual Studio est en cours d’arrêt ou un autre package a repris le dessus comme le Gestionnaire de chargement de solution active en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> avec le <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propriété.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Stratégies pour différents types de gestionnaire de chargement de solution  
 Vous pouvez implémenter des gestionnaires de chargement de solution de différentes manières, selon les types de solutions qu’ils sont destinés à gérer.  
  
 Si le Gestionnaire de chargement de solution est destiné à gérer le chargement en général, elle peut être implémentée en tant que partie d’un VSPackage. Le package doit être défini pour le chargement automatique en ajoutant le <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> sur le VSPackage avec la valeur <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Le Gestionnaire de chargement de solution peut ensuite être activé dans le <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> (méthode).  
  
> [!NOTE]
>  Pour plus d’informations sur les packages de chargement automatique, consultez [le chargement de VSPackages](../extensibility/loading-vspackages.md).  
  
 Dans la mesure où Visual Studio reconnaît uniquement le Gestionnaire de charge solution dernier à être activé, gestionnaires de chargement de solution générale doivent toujours détecter la présence d’un gestionnaire de charge existant avant d’activer eux-mêmes. Si l’appel `GetProperty()` sur le service de la solution pour <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> retourne `null`, il n’existe aucun gestionnaire de chargement de solution active. Si elle ne retourne pas null, vérifiez si l’objet est le même que le Gestionnaire de charge de votre solution.  
  
 Si le Gestionnaire de chargement de solution est destiné à ne gérer que quelques types de solution, le VSPackage peut s’abonner aux événements de chargement de solution (en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) et utiliser le Gestionnaire d’événements pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> pour activer le Gestionnaire de chargement de solution.  
  
 Si le Gestionnaire de chargement de solution est destiné à gérer des solutions spécifiques, les informations d’activation peuvent être rendu persistant dans le cadre du fichier solution en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> pour la section de pré-solution.  
  
 Gestionnaires de chargement de solution spécifique doivent se désactiver eux-mêmes dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> Gestionnaire d’événements, afin de ne pas entrer en conflit avec d’autres gestionnaires de chargement de solution.  
  
 Si vous avez besoin d’un gestionnaire de chargement de solution uniquement pour conserver les propriétés de charge de projets globale (par exemple, les propriétés définies sur une page d’Options), vous pouvez activer le Gestionnaire de chargement de solution dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> Gestionnaire d’événements, conserver le paramètre dans les propriétés de la solution, puis désactiver le Gestionnaire de chargement de solution.  
  
## <a name="handle-solution-load-events"></a>Gérer les événements de chargement de solution  
 Pour vous abonner aux événements de chargement de solution, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> lorsque vous activez le Gestionnaire de charge de votre solution. Si vous implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, vous pouvez répondre aux événements liés à un projet différent du chargement des propriétés.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Cet événement est déclenché avant l’ouverture d’une solution.
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Cet événement est déclenché une fois la solution est entièrement chargée, mais avant d’arrière-plan le chargement du projet commence à nouveau.
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Cet événement est déclenché une fois une solution est initialement entièrement chargée, s’il existe un gestionnaire de chargement de solution. Il est également déclenché après chargement de l’arrière-plan ou à la demande chargé chaque fois que la solution devienne complètement chargée. En même temps, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> est réactivé.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Cet événement est déclenché avant le chargement d’un projet (ou projets). Pour vous assurer que les autres processus d’arrière-plan sont terminées avant que les projets sont chargés, définissez `pfShouldDelayLoadToNextIdle` à **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Cet événement est déclenché lorsqu’un lot de projets est sur le point d’être chargé. Si `fIsBackgroundIdleBatch` a la valeur true, les projets doivent être chargés en arrière-plan ; si `fIsBackgroundIdleBatch` a la valeur false, les projets doivent être chargés de façon synchrone à la suite d’une demande d’utilisateur, par exemple si l’utilisateur développe un projet en attente dans l’Explorateur de solutions. Vous pouvez gérer cet événement pour faire le travail coûteux qui sinon devraient être effectuée dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Cet événement est déclenché après le chargement d’un lot de projets.  
  
## <a name="detect-and-manage-solution-and-project-loading"></a>Détecter et gérer la solution et du chargement de projet  
 Afin de détecter l’état de chargement des projets et solutions, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> avec les valeurs suivantes :  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retourne `true` si la solution et tous ses projets sont chargés, sinon `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retourne `true` si un lot de projets est actuellement chargé en arrière-plan, sinon `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retourne `true` si un lot de projets est actuellement en cours chargé de façon synchrone en raison d’une commande de l’utilisateur ou autres chargement explicite, sinon `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` retourne `true` si la solution est actuellement en cours fermée, sinon `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` retourne `true` si une solution est actuellement en cours d’ouverture, sinon `false`.  
  
  Vous pouvez également vous assurer que les projets et solutions sont chargées en appelant une des méthodes suivantes :  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: cette méthode force les projets dans une solution de chargement avant le retour de la méthode.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: cette méthode force les projets de `guidProject` chargement avant le retour de la méthode.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: cette méthode force le projet dans `guidProjectID` chargement avant le retour de la méthode.  
