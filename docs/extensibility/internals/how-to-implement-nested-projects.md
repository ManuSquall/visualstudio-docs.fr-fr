---
title: 'Comment : implémenter des projets imbriqués | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b1ac3c147962b943499172435c3f601115d36a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905352"
---
# <a name="how-to-implement-nested-projects"></a>Comment : implémenter des projets imbriqués

Lorsque vous créez un type de projet imbriqué, plusieurs étapes supplémentaires doivent être implémentées. Un projet parent prend en compte les mêmes responsabilités que celles de la solution pour ses projets imbriqués (enfants). Le projet parent est un conteneur de projets similaire à une solution. En particulier, il existe plusieurs événements qui doivent être déclenchés par la solution et par les projets parents pour générer la hiérarchie des projets imbriqués. Ces événements sont décrits dans le processus suivant pour créer des projets imbriqués.

## <a name="create-nested-projects"></a>Créer des projets imbriqués

1. L’environnement de développement intégré (IDE) charge le fichier projet du projet parent et les informations de démarrage en appelant l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interface. Le projet parent est créé et ajouté à la solution.

    > [!NOTE]
    > À ce stade, il est trop tôt dans le processus pour que le projet parent crée le projet imbriqué, car le projet parent doit être créé avant que les projets enfants puissent être créés. À la suite de cette séquence, le projet parent peut appliquer des paramètres aux projets enfants et les projets enfants peuvent obtenir des informations à partir des projets parents, si nécessaire. Cette séquence est si nécessaire sur les clients tels que le contrôle de code source (SCC) et **Explorateur de solutions**.

     Le projet parent doit attendre que la <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> méthode soit appelée par l’IDE avant de pouvoir créer son ou ses projets imbriqués (enfants).

2. L’IDE appelle `QueryInterface` sur le projet parent pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject> . Si cet appel a échoué, l’IDE appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> méthode du parent pour ouvrir tous les projets imbriqués pour le projet parent.

3. Le projet parent appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> méthode pour notifier les écouteurs de la création des projets imbriqués. SCC, par exemple, écoute les événements pour savoir si les étapes du processus de création de la solution et du projet se produisent dans l’ordre. Si les étapes se produisent dans le désordre, la solution n’est peut-être pas inscrite correctement avec le contrôle de code source.

4. Le projet parent appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> méthode ou la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> méthode sur chacun de ses projets enfants.

     Vous transmettez <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> à la `AddVirtualProject` méthode pour indiquer que le projet virtuel (imbriqué) doit être ajouté à la fenêtre du projet, exclu de la génération, ajouté au contrôle de code source, et ainsi de suite. `VSADDVPFLAGS` vous permet de contrôler la visibilité du projet imbriqué et d’indiquer les fonctionnalités qui lui sont associées.

     Si vous rechargez un projet enfant existant qui a un GUID de projet stocké dans le fichier projet du projet parent, le projet parent appelle `AddVirtualProjectEx` . La seule différence entre `AddVirtualProject` et `AddVirtualProjectEX` est que `AddVirtualProjectEX` a un paramètre pour permettre au projet parent de spécifier un par instance `guidProjectID` pour que le projet enfant active <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> fonctionne correctement.

     Si aucun GUID n’est disponible, par exemple lorsque vous ajoutez un nouveau projet imbriqué, la solution en crée un pour le projet au moment où il est ajouté au parent. Il incombe au projet parent de conserver ce GUID de projet dans son fichier projet. Si vous supprimez un projet imbriqué, le GUID de ce projet peut également être supprimé.

5. L’IDE appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> méthode sur chaque projet enfant du projet parent.

     Le projet parent doit implémenter `IVsParentProject` si vous souhaitez imbriquer des projets. Toutefois, le projet parent n’appelle jamais `QueryInterface` pour `IVsParentProject` , même s’il a des projets parents en dessous. La solution gère l’appel à `IVsParentProject` et, si elle est implémentée, appelle `OpenChildren` pour créer les projets imbriqués. `AddVirtualProjectEX` est toujours appelé à partir de `OpenChildren` . Elle ne doit jamais être appelée par le projet parent pour conserver les événements de création de hiérarchie dans l’ordre.

6. L’IDE appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> méthode sur le projet enfant.

7. Le projet parent appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> méthode pour notifier les écouteurs que les projets enfants pour le parent ont été créés.

8. L’IDE appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> méthode sur le projet parent une fois tous les projets enfants ouverts.

     S’il n’existe pas déjà, le projet parent crée un GUID pour chaque projet imbriqué en appelant `CoCreateGuid` .

    > [!NOTE]
    > `CoCreateGuid` est une API COM appelée lorsqu’un GUID doit être créé. Pour plus d’informations, consultez `CoCreateGuid` et GUID dans MSDN Library.

     Le projet parent stocke ce GUID dans son fichier projet à récupérer la prochaine fois qu’il est ouvert dans l’IDE. Pour plus d’informations sur l’appel de `AddVirtualProjectEX` pour récupérer le `guidProjectID` pour le projet enfant, consultez l’étape 4.

9. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> méthode est ensuite appelée pour le ItemId parent, par convention que vous déléguez au projet imbriqué. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>Récupère les propriétés du nœud qui imbrique un projet que vous souhaitez déléguer lorsqu’il est appelé sur le parent.

     Étant donné que les projets parents et enfants sont instanciés par programme, vous pouvez définir des propriétés pour les projets imbriqués à ce stade.

    > [!NOTE]
    > Non seulement vous recevez les informations de contexte à partir du projet imbriqué, mais vous pouvez également demander si le projet parent possède un contexte pour cet élément en vérifiant [__VSHPROPID. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). De cette façon, vous pouvez ajouter des attributs d’aide dynamique supplémentaires et des options de menu spécifiques à des projets imbriqués individuels.

10. La hiérarchie est générée pour s’afficher dans **Explorateur de solutions** avec un appel à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> méthode.

     Vous transmettez la hiérarchie à l’environnement par le biais `GetNestedHierarchy` de pour créer la hiérarchie à afficher dans Explorateur de solutions. De cette manière, la solution sait que le projet existe et peut être géré pour être généré par le gestionnaire de build, ou peut permettre aux fichiers du projet d’être placés sous contrôle de code source.

11. Lorsque tous les projets imbriqués pour Projet1 ont été créés, le contrôle est renvoyé à la solution et le processus est répété pour project2.

     Pour créer des projets imbriqués, le même processus se produit pour un projet enfant qui a un enfant. Dans ce cas, si BuildProject1, qui est un enfant de Project1, avait des projets enfants, il serait créé après BuildProject1 et avant project2. Le processus est récursif et la hiérarchie est créée de haut en haut.

     Quand un projet imbriqué est fermé parce que l’utilisateur a fermé la solution ou le projet spécifique lui-même, l’autre méthode sur `IVsParentProject` , <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A> , est appelée. Le projet parent encapsule les appels à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> méthode avec les <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> méthodes et pour notifier les écouteurs aux événements de solution que les projets imbriqués sont fermés.

Les rubriques suivantes traitent de plusieurs autres concepts à prendre en compte lorsque vous implémentez des projets imbriqués :

- [Considérations sur le déchargement et le rechargement des projets imbriqués](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Prise en charge de l’Assistant pour les projets imbriqués](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Implémenter la gestion des commandes pour les projets imbriqués](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrer la boîte de dialogue AddItem pour les projets imbriqués](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Voir aussi

- [Ajouter des éléments à la boîte de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Inscrire des modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)
- [Liste de vérification : créer des types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Paramètres de contexte](../../extensibility/internals/context-parameters.md)
- [Fichier Assistant (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
