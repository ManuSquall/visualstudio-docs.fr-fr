---
title: Gérer le chargement de projets dans une solution . Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21cd5e7e557e795db49aea7a14e8e4cc7caa0422
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702734"
---
# <a name="manage-project-loading-in-a-solution"></a>Gérer le chargement du projet dans une solution
Les solutions Visual Studio peuvent contenir un grand nombre de projets. Le comportement par défaut visual Studio est de charger tous les projets dans une solution au moment où la solution est ouverte, et de ne pas permettre à l’utilisateur d’accéder à l’un des projets jusqu’à ce que tous ont terminé le chargement. Lorsque le processus de chargement du projet durera plus de deux minutes, une barre de progression est affichée montrant le nombre de projets chargés et le nombre total de projets. L’utilisateur peut décharger des projets tout en travaillant dans une solution avec plusieurs projets, mais cette procédure présente quelques inconvénients : les projets déchargés ne sont pas construits dans le cadre d’une commande Rebuild Solution, et les descriptions IntelliSense des types et des membres de projets fermés ne sont pas affichées.

 Les développeurs peuvent réduire les temps de chargement des solutions et gérer le comportement de chargement de projet en créant un gestionnaire de charge de solution. Le gestionnaire de chargement de solution peut s’assurer que les projets sont chargés avant de commencer une construction d’arrière-plan, retarder le chargement de fond jusqu’à ce que d’autres tâches d’arrière-plan soient terminées et effectuer d’autres tâches de gestion de la charge de projet.

## <a name="create-a-solution-load-manager"></a>Créer un gestionnaire de charge de solution
 Les développeurs peuvent créer un <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> gestionnaire de charge de solution en implémentant et en informant Visual Studio que le gestionnaire de charge de solution est actif.

### <a name="activate-a-solution-load-manager"></a>Activer un gestionnaire de charge de solution
 Visual Studio n’autorise qu’un seul gestionnaire de charge de solution à un moment donné, vous devez donc conseiller Visual Studio lorsque vous souhaitez activer votre gestionnaire de charge de solution. Si un deuxième gestionnaire de charge de solution est activé plus tard, votre gestionnaire de charge de solution sera déconnecté.

 Vous devez <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> obtenir le service et définir le [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) bien:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 La <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> méthode est appelée soit lorsque Visual Studio est arrêté ou quand un paquet <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> différent a pris le relais en tant que gestionnaire de charge de solution active en appelant avec le [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) bien.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Stratégies pour différents types de gestionnaire de charge de solution
 Vous pouvez implémenter des gestionnaires de charge de solutions de différentes manières, en fonction des types de solutions qu’ils sont censés gérer.

 Si le gestionnaire de charge de solution est destiné à gérer le chargement de solution en général, il peut être implémenté dans le cadre d’un VSPackage. Le paquet doit être réglé à <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> l’autochargement en <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>ajoutant le sur le VSPackage avec une valeur de . Le gestionnaire de charge de <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> solution peut alors être activé dans la méthode.

> [!NOTE]
> Pour plus d’informations sur les paquets de recharge automatique, voir [Chargement VSPackages](../extensibility/loading-vspackages.md).

 Étant donné que Visual Studio ne reconnaît que le dernier gestionnaire de charge de solution à être activé, les gestionnaires généraux de chargement de solutions doivent toujours détecter s’il existe un gestionnaire de charge existant avant de s’activer. Si `GetProperty()` vous appelez le service de solution pour [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager revient,](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) `null`il n’y a pas de gestionnaire de charge de solution actif. S’il ne retourne pas nul, vérifiez si l’objet est le même que votre gestionnaire de charge de solution.

 Si le gestionnaire de charge de solution est destiné à gérer seulement quelques types de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>solution, le VSPackage peut s’abonner à des événements de charge de solution (en appelant ), et utiliser le gestionnaire d’événement pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> activer le gestionnaire de charge de solution.

 Si le gestionnaire de chargement de solution est destiné à gérer uniquement des solutions <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> spécifiques, les informations d’activation peuvent être persistées dans le cadre du fichier de solution en appelant à la section pré-solution.

 Les gestionnaires spécifiques de chargement <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> de solution devraient se désactiver dans le gestionnaire d’événement, afin de ne pas entrer en conflit avec d’autres gestionnaires de charge de solution.

 Si vous avez besoin d’un gestionnaire de charge de solution uniquement pour maintenir les propriétés globales de chargement de projet (par exemple, les propriétés définies sur une page Options), vous pouvez activer le gestionnaire de charge de solution dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> gestionnaire d’événement, persister le paramètre dans les propriétés de la solution, puis désactiver le gestionnaire de charge de solution.

## <a name="handle-solution-load-events"></a>Gérer les événements de chargement de solution
 Pour vous abonner <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> aux événements de chargement de solution, appelez lorsque vous activez votre gestionnaire de charge de solution. Si vous <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>implémentez, vous pouvez répondre à des événements qui se rapportent à différentes propriétés de chargement de projet.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Cet événement est déclenché avant l’ouverture d’une solution.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Cet événement est déclenché après que la solution est complètement chargée, mais avant que le chargement du projet d’arrière-plan ne recommence.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Cet événement est déclenché après qu’une solution soit initialement entièrement chargée, qu’il y ait ou non un gestionnaire de charge de solution. Il est également tiré après la charge de fond ou la charge de la demande chaque fois que la solution devient entièrement chargée. En même temps, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> est réactivé.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Cet événement est déclenché avant le chargement d’un projet (ou de projets). Pour s’assurer que d’autres processus d’arrière-plan sont terminés avant que les projets soient chargés, définis comme `pfShouldDelayLoadToNextIdle` **vrais**.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Cet événement est déclenché lorsqu’un lot de projets est sur le point d’être chargé. Si `fIsBackgroundIdleBatch` c’est vrai, les projets doivent être chargés en arrière-plan; s’il `fIsBackgroundIdleBatch` est faux, les projets doivent être chargés de manière synchrone à la suite d’une demande d’utilisateur, par exemple si l’utilisateur élargit un projet en attente dans Solution Explorer. Vous pouvez gérer cet événement pour faire un travail <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>coûteux qui autrement aurait besoin d’être fait en .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Cet événement est déclenché après qu’un lot de projets a été chargé.

## <a name="detect-and-manage-solution-and-project-loading"></a>Détecter et gérer le chargement des solutions et des projets
 Afin de détecter l’état de chargement des projets et des solutions, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> avec les valeurs suivantes :

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>): `var` revient `true` si la solution et tous `false`ses projets sont chargés, sinon.

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>): `var` revient `true` si un lot de projets est `false`actuellement chargé en arrière-plan, sinon.

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>): `var` revient `true` si un lot de projets est actuellement chargé de façon synchrone `false`à la suite d’une commande utilisateur ou d’une autre charge explicite, autrement .

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>): `var` revient `true` si la solution est `false`actuellement fermée, sinon .

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>): `var` revient `true` si une solution est `false`en cours d’ouverture, sinon .

Vous pouvez également vous assurer que les projets et les solutions sont chargés en appelant l’une des méthodes suivantes :

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: l’appel de cette méthode force les projets dans une solution à charger avant le retour de la méthode.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: l’appel de `guidProject` cette méthode oblige les projets à charger avant le retour de la méthode.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: appeler cette méthode `guidProjectID` force le projet à charger avant le retour de la méthode.
