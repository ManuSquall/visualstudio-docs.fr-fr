---
title: 'Comment : Mettre en œuvre des projets imbriqués Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d9dfe567db0b8788b93b13aeb760d45f4c05b57
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707983"
---
# <a name="how-to-implement-nested-projects"></a>Comment : Mettre en œuvre des projets imbriqués

Lorsque vous créez un type de projet imbriqué, il y a plusieurs étapes supplémentaires qui doivent être mises en œuvre. Un projet parent assume certaines des mêmes responsabilités que la solution pour ses projets imbriqués (enfants). Le projet parent est un conteneur de projets semblables à une solution. En particulier, il y a plusieurs événements qui doivent être soulevés par la solution et par les projets parentaux pour construire la hiérarchie des projets imbriqués. Ces événements sont décrits dans le processus suivant pour la création de projets imbriqués.

## <a name="create-nested-projects"></a>Créer des projets imbriqués

1. L’environnement de développement intégré (IDE) charge le dossier de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> projet et les informations de démarrage du projet parent en appelant l’interface. Le projet parent est créé et ajouté à la solution.

    > [!NOTE]
    > À ce stade, il est trop tôt dans le processus pour le projet parent de créer le projet imbriqué parce que le projet parent doit être créé avant que les projets pour enfants puissent être créés. À la suite de cette séquence, le projet parent peut appliquer des paramètres aux projets pour enfants et les projets pour enfants peuvent obtenir de l’information auprès des projets parentaux si nécessaire. Cette séquence est si elle est nécessaire sur par les clients tels que le contrôle du code source (SCC) et **Solution Explorer**.

     Le projet parent doit <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> attendre que la méthode soit appelée par l’IDE avant de pouvoir créer son projet ou projets imbriqués (enfant).

2. L’IDE `QueryInterface` fait appel <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>au projet parent pour . Si cet appel réussit, l’IDE appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> méthode du parent pour ouvrir tous les projets imbriqués pour le projet parent.

3. Le projet parent <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> appelle la méthode pour aviser les auditeurs que les projets imbriqués sont sur le point d’être créés. SCC, par exemple, est à l’écoute de ces événements pour savoir si les étapes du processus de création de solutions et de projets sont en ordre. Si les étapes sont hors d’état de la marche, la solution peut ne pas être enregistrée correctement avec le contrôle du code source.

4. Le projet <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> parent appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> la méthode ou la méthode sur chacun de ses projets pour enfants.

     Vous passez <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> à `AddVirtualProject` la méthode pour indiquer que le projet virtuel (imbriqué) doit être ajouté à la fenêtre du projet, exclu de la construction, ajouté au contrôle du code source, et ainsi de suite. `VSADDVPFLAGS`vous permet de contrôler la visibilité du projet imbriqué et d’indiquer quelles fonctionnalités y sont associées.

     Si vous rechargez un projet d’enfant déjà existant qui a un projet GUID `AddVirtualProjectEx`stocké dans le dossier de projet du projet parent, le projet parent appelle . La seule `AddVirtualProject` différence `AddVirtualProjectEX` entre `AddVirtualProjectEX` et est celle qui a un `guidProjectID` paramètre pour permettre <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> au projet parent de spécifier un par exemple pour le projet enfant pour activer et fonctionner correctement.

     S’il n’y a pas de GUID disponible, par exemple lorsque vous ajoutez un nouveau projet imbriqué, la solution en crée une pour le projet au moment où elle est ajoutée au parent. Il incombe au projet parent de poursuivre ce projet GUID dans son dossier de projet. Si vous supprimez un projet imbriqué, le GUID pour ce projet peut également être supprimé.

5. L’IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> appelle la méthode sur chaque projet enfant du projet parent.

     Le projet parent `IVsParentProject` doit être mis en œuvre si vous voulez nicher des projets. Mais le projet `QueryInterface` parent `IVsParentProject` n’exige jamais, même s’il a des projets parentaux en dessous. La solution gère l’appel vers `IVsParentProject` et, `OpenChildren` s’il est mis en œuvre, appelle à créer les projets imbriqués. `AddVirtualProjectEX`est toujours `OpenChildren`appelé de . Il ne devrait jamais être appelé par le projet parent pour maintenir les événements de création de hiérarchie en ordre.

6. L’IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> appelle la méthode sur le projet enfant.

7. Le projet parent <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> appelle la méthode pour informer les auditeurs que les projets pour enfants pour le parent ont été créés.

8. L’IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> appelle la méthode sur le projet parent après que tous les projets d’enfants ont été ouverts.

     S’il n’existe pas déjà, le projet parent crée `CoCreateGuid`un GUID pour chaque projet imbriqué en appelant .

    > [!NOTE]
    > `CoCreateGuid`est une API COM appelée lorsqu’un GUID doit être créé. Pour plus d’informations, voir `CoCreateGuid` et GUIDs dans la bibliothèque MSDN.

     Le projet parent stocke cette GUID dans son dossier de projet pour être récupéré la prochaine fois qu’il est ouvert dans l’IDE. Voir l’étape 4 pour plus `AddVirtualProjectEX` d’informations sur l’appel de récupérer le `guidProjectID` projet pour l’enfant.

9. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> méthode est alors demandée pour le parent ItemID que par convention vous déléguez dans le projet imbriqué. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> récupère les propriétés du nœud qui niche un projet que vous voulez déléguer quand il est appelé sur le parent.

     Étant donné que les projets parent et enfant sont instantanés sur le plan programmatique, vous pouvez définir des propriétés pour des projets imbriqués à ce stade.

    > [!NOTE]
    > Non seulement vous recevez l’information contextuelle du projet imbriqué, mais vous pouvez également demander si le projet parent a un contexte pour cet article en vérifiant [__VSHPROPID. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). De cette façon, vous pouvez ajouter des attributs d’aide dynamique supplémentaires et des options de menu spécifiques aux projets imbriqués individuels.

10. La hiérarchie est conçue pour l’affichage <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> dans Solution **Explorer** avec un appel à la méthode.

     Vous passez la hiérarchie à `GetNestedHierarchy` l’environnement à travers pour construire la hiérarchie pour l’affichage dans Solution Explorer. De cette manière, la solution sait que le projet existe et peut être géré pour la construction par le gestionnaire de construction, ou peut permettre aux fichiers dans le projet d’être mis sous contrôle de code source.

11. Lorsque tous les projets imbriqués pour le projet1 ont été créés, le contrôle est transmis à la solution et le processus est répété pour le projet2.

     Ce même processus de création de projets imbriqués se produit pour un projet pour enfants qui a un enfant. Dans ce cas, si BuildProject1, qui est un enfant du projet1, avait des projets pour enfants, ils seraient créés après BuildProject1 et avant Project2. Le processus est récursif et la hiérarchie est construite de haut en bas.

     Lorsqu’un projet imbriqué est fermé parce que l’utilisateur a `IVsParentProject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>fermé la solution ou le projet spécifique lui-même, l’autre méthode sur , , est appelé. Le projet parent enveloppe <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> les appels <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> à <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> la méthode avec le et les méthodes pour informer les auditeurs de solutions événements que les projets imbriqués sont en cours de fermeture.

Les sujets suivants traitent de plusieurs autres concepts à considérer lorsque vous mettez en œuvre des projets imbriqués :

- [Considérations pour le déchargement et le rechargement des projets imbriqués](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Soutien des sorciers pour les projets imbriqués](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Mettre en œuvre la gestion des commandes pour les projets imbriqués](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrer la boîte de dialogue AddItem pour les projets imbriqués](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Voir aussi

- [Ajouter des éléments à la boîte de dialogue Add New Item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Enregistrer les modèles de projets et d’objets](../../extensibility/internals/registering-project-and-item-templates.md)
- [Liste de contrôle : Créer de nouveaux types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Paramètres de contexte](../../extensibility/internals/context-parameters.md)
- [Fichier Wizard (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
