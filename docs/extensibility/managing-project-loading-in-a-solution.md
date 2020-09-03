---
title: Gestion du chargement de projet dans une solution | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702734"
---
# <a name="manage-project-loading-in-a-solution"></a>Gérer le chargement du projet dans une solution
Les solutions Visual Studio peuvent contenir un grand nombre de projets. Le comportement de Visual Studio par défaut consiste à charger tous les projets d’une solution au moment de l’ouverture de la solution, et non à permettre à l’utilisateur d’accéder à tous les projets jusqu’à ce qu’ils aient terminé le chargement. Lorsque le processus de chargement du projet dure plus de deux minutes, une barre de progression s’affiche, affichant le nombre de projets chargés et le nombre total de projets. L’utilisateur peut décharger des projets tout en travaillant dans une solution avec plusieurs projets, mais cette procédure présente quelques inconvénients : les projets déchargés ne sont pas générés dans le cadre d’une commande Rebuild solution, et les descriptions IntelliSense des types et des membres des projets fermés ne sont pas affichées.

 Les développeurs peuvent réduire le temps de chargement de la solution et gérer le comportement de chargement du projet en créant un gestionnaire de chargement de solution. Le gestionnaire de chargement de solution peut s’assurer que les projets sont chargés avant le démarrage d’une build en arrière-plan, retarder le chargement en arrière-plan jusqu’à ce que les autres tâches en arrière-plan soient terminées et effectuer d’autres tâches de gestion

## <a name="create-a-solution-load-manager"></a>Créer un gestionnaire de chargement de solution
 Les développeurs peuvent créer un gestionnaire de chargement de solution en implémentant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> et en conseillant à Visual Studio que le gestionnaire de chargement de solution est actif.

### <a name="activate-a-solution-load-manager"></a>Activer un gestionnaire de chargement de solution
 Visual Studio n’autorise qu’un seul gestionnaire de chargement de solution à un moment donné. vous devez donc conseiller Visual Studio lorsque vous souhaitez activer votre gestionnaire de chargement de solution. Si un deuxième gestionnaire de chargement de solution est activé ultérieurement, votre gestionnaire de chargement de solution sera déconnecté.

 Vous devez avoir le <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> service et définir la [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) propriété :

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 La <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> méthode est appelée lorsque Visual Studio est arrêté ou lorsqu’un autre package est pris en charge en tant que gestionnaire de chargement de solution actif en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> avec l' [__VSPROPID4. Propriété VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) .

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Stratégies pour différents types de gestionnaires de chargement de solution
 Vous pouvez implémenter des gestionnaires de chargement de solution de différentes manières, selon les types de solutions qu’ils sont censés gérer.

 Si le gestionnaire de chargement de solution est destiné à gérer le chargement de solution en général, il peut être implémenté dans le cadre d’un VSPackage. Le package doit être défini sur autoload en ajoutant le <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> sur le VSPackage avec la valeur <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . Le gestionnaire de chargement de solution peut ensuite être activé dans la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode.

> [!NOTE]
> Pour plus d’informations sur le chargement automatique des packages, consultez [chargement des VSPackages](../extensibility/loading-vspackages.md).

 Étant donné que Visual Studio ne reconnaît que le dernier gestionnaire de chargement de solution à activer, les gestionnaires de charge de solution généraux doivent toujours déterminer s’il existe un gestionnaire de chargement avant de l’activer. Si vous appelez `GetProperty()` sur le service de solution pour [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) retourne `null` , il n’y a aucun gestionnaire de chargement de solution actif. Si elle ne retourne pas de valeur null, vérifiez si l’objet est identique à celui de votre gestionnaire de chargement de solution.

 Si le gestionnaire de chargement de solution est destiné à gérer uniquement quelques types de solution, le VSPackage peut s’abonner aux événements de chargement de solution (en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ) et utiliser le gestionnaire d’événements pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> activer le gestionnaire de chargement de solution.

 Si le gestionnaire de chargement de solution est destiné à gérer uniquement des solutions spécifiques, les informations d’activation peuvent être rendues persistantes dans le cadre du fichier solution en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> pour la section pré-solution.

 Les gestionnaires de chargement de solution spécifiques doivent être désactivés dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> Gestionnaire d’événements, afin de ne pas entrer en conflit avec d’autres gestionnaires de chargement de solution.

 Si vous avez besoin d’un gestionnaire de chargement de solution uniquement pour rendre persistantes les propriétés de chargement global d’un projet (par exemple, les propriétés définies sur une page d’options), vous pouvez activer le gestionnaire de chargement de solution dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> Gestionnaire d’événements, le rendre persistant dans les propriétés de la solution, puis désactiver le gestionnaire de chargement de solution.

## <a name="handle-solution-load-events"></a>Gérer les événements de chargement de solution
 Pour vous abonner aux événements de chargement de solution, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> quand vous activez votre gestionnaire de chargement de solution. Si vous implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> , vous pouvez répondre aux événements liés à différentes propriétés de chargement de projet.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Cet événement est déclenché avant l’ouverture d’une solution.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Cet événement est déclenché après le chargement complet de la solution, mais avant le redémarrage du projet en arrière-plan.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Cet événement est déclenché après le chargement initial complet d’une solution, qu’il s’agisse ou non d’un gestionnaire de chargement de solution. Elle est également déclenchée après le chargement en arrière-plan ou la charge de la demande chaque fois que la solution est entièrement chargée. En même temps, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> est réactivé.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Cet événement est déclenché avant le chargement d’un projet (ou de projets). Pour vous assurer que les autres processus en arrière-plan sont terminés avant le chargement des projets, affectez à la valeur `pfShouldDelayLoadToNextIdle` **true**.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Cet événement est déclenché lorsqu’un lot de projets est sur le lieu d’être chargé. Si `fIsBackgroundIdleBatch` a la valeur true, les projets doivent être chargés en arrière-plan ; si `fIsBackgroundIdleBatch` a la valeur false, les projets doivent être chargés de façon synchrone à la suite d’une demande de l’utilisateur, par exemple, si l’utilisateur développe un projet en attente dans Explorateur de solutions. Vous pouvez gérer cet événement pour effectuer des tâches coûteuses qui, autrement, auraient besoin d’être effectuées dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Cet événement est déclenché après le chargement d’un lot de projets.

## <a name="detect-and-manage-solution-and-project-loading"></a>Détection et gestion du chargement de solutions et de projets
 Pour détecter l’état de chargement des projets et des solutions, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> avec les valeurs suivantes :

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>): `var` retourne `true` si la solution et tous ses projets sont chargés ; sinon, `false` .

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>): `var` retourne `true` si un lot de projets est actuellement en cours de chargement en arrière-plan ; sinon, `false` .

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>): `var` retourne `true` si un lot de projets est actuellement chargé en mode synchrone à la suite d’une commande utilisateur ou d’un autre chargement explicite, sinon `false` .

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>): `var` retourne `true` si la solution est en cours de fermeture ; sinon, `false` .

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>): `var` retourne `true` si une solution est actuellement ouverte ; sinon, `false` .

Vous pouvez également vous assurer que les projets et les solutions sont chargés en appelant l’une des méthodes suivantes :

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: l’appel de cette méthode force le chargement des projets dans une solution avant le retour de la méthode.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: l’appel de cette méthode force le `guidProject` chargement des projets avant le retour de la méthode.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: l’appel de cette méthode force le `guidProjectID` chargement du projet avant le retour de la méthode.
