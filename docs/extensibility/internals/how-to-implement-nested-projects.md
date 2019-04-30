---
title: 'Procédure : Implémenter des projets imbriqués | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96df14cc6e337402761d89d7161094b513473a78
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62860761"
---
# <a name="how-to-implement-nested-projects"></a>Procédure : Implémenter des projets imbriqués

Lorsque vous créez un type de projet imbriqué, il existe plusieurs étapes supplémentaires qui doivent être implémentées. Un projet parent prend en charge certaines responsabilités de mêmes que la solution dispose de ses projets imbriqués (enfants). Le projet parent est un conteneur de projets similaires à une solution. En particulier, il existe plusieurs événements qui doivent être déclenchés par la solution et par les projets parent pour générer la hiérarchie de projets imbriqués. Ces événements sont décrits dans le processus suivant pour la création de projets imbriqués.

## <a name="create-nested-projects"></a>Créer des projets imbriqués

1. L’environnement de développement intégré (IDE) charge les informations de démarrage et le fichier de projet du projet parent en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interface. Le projet parent est créé et ajouté à la solution.

    > [!NOTE]
    > À ce stade, il est trop tôt dans le processus pour le projet parent créer le projet imbriqué, car le projet parent doit être créé avant de pouvoir créer les projets enfants. Après cette séquence, le projet parent peut appliquer les paramètres pour les projets enfants et les projets enfants peuvent acquérir des informations à partir des projets parent si nécessaire. Cette séquence est si elle est nécessaire par les clients comme contrôle de code source (SCC) et **l’Explorateur de solutions**.

     Le projet parent doit attendre le <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> méthode doit être appelée par l’IDE avant de pouvoir créer son imbriqués (enfants) ou les projets.

2. Les appels IDE `QueryInterface` sur le projet parent pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>. Si cet appel réussit, les appels de l’IDE le <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> méthode du parent pour ouvrir tous les projets imbriqués pour le projet parent.

3. Les appels de projet parent le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> méthode pour informer les écouteurs qui imbriquée des projets doivent être créés. Contrôle de code source, par exemple, est à l’écoute à ces événements afin de savoir si les étapes décrites dans le processus de création de projet et solution sont produisent dans l’ordre. Si les étapes se produisent en désordre, la solution ne soit pas enregistrée avec le contrôle de code source correctement.

4. Les appels de projet parent <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> méthode ou le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> méthode sur chacun de ses projets enfants.

     Vous transmettez <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> à la `AddVirtualProject` méthode pour indiquer que le projet virtuel (imbriqué) doit être ajouté à la fenêtre de projet, exclue de la génération, ajouté au contrôle de code source et ainsi de suite. `VSADDVPFLAGS` vous permet de contrôler la visibilité du projet imbriqué et indiquer quelles sont les fonctionnalités lui sont associée.

     Si vous rechargez un projet enfant existant qui possède un GUID stocké dans le fichier de projet du projet parent, les appels de projet parent du projet `AddVirtualProjectEx`. La seule différence entre `AddVirtualProject` et `AddVirtualProjectEX` qui est `AddVirtualProjectEX` a un paramètre pour activer le projet parent spécifier un par instance `guidProjectID` pour le projet enfant pour activer <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> à (fonction) correctement.

     Si aucun GUID n’est disponible, comme lorsque vous ajoutez un nouveau projet imbriqué, la solution crée un pour le projet au moment où il est ajouté au parent. Il est la responsabilité du projet parent pour conserver ce GUID du projet dans son fichier de projet. Si vous supprimez un projet imbriqué, le GUID de ce projet peut également être supprimé.

5. Les appels de l’IDE le <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> méthode sur chaque projet enfant du projet parent.

     Le projet parent doit implémenter `IVsParentProject` si vous souhaitez imbriquer des projets. Mais le parent du projet jamais appels `QueryInterface` pour `IVsParentProject` même s’il possède des projets parent situé en dessous. La solution gère l’appel à `IVsParentProject` et, si elle est implémentée, il appelle `OpenChildren` pour créer des projets imbriqués. `AddVirtualProjectEX` est toujours appelée à partir de `OpenChildren`. Il ne doit jamais être appelée par le projet parent pour conserver des événements de la création de la hiérarchie dans l’ordre.

6. Les appels de l’IDE le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> méthode sur le projet enfant.

7. Les appels de projet parent le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> méthode pour informer les écouteurs que les projets enfants du parent ont été créés.

8. Les appels de l’IDE le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> méthode sur le projet parent une fois que tous les projets enfants ont été ouverts.

     Si elle n’existe pas déjà, le projet parent crée un GUID pour chaque projet imbriqué en appelant `CoCreateGuid`.

    > [!NOTE]
    > `CoCreateGuid` est une API COM appelée quand un GUID doit être créé. Pour plus d’informations, consultez `CoCreateGuid` et les GUID dans MSDN Library.

     Le projet parent stocke ce GUID dans son fichier de projet à récupérer la prochaine fois qu’il est ouvert dans l’IDE. Consultez l’étape 4 pour plus d’informations relatives à l’appel de `AddVirtualProjectEX` pour récupérer le `guidProjectID` pour le projet enfant.

9. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> méthode est ensuite appelée pour le parent ItemID par convention déléguer le dans pour le projet imbriqué. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> récupère les propriétés du nœud qui imbrique un projet que vous souhaitez déléguer dans lorsqu’elle est appelée sur le parent.

     Étant donné que les projets parents et enfants sont instanciés par programmation, vous pouvez définir des propriétés pour les projets imbriqués à ce stade.

    > [!NOTE]
    > Non seulement vous recevez les informations de contexte à partir du projet imbriqué, mais vous pouvez également demander si le projet parent a n’importe quel contexte de cet élément en vérifiant [__VSHPROPID. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). De cette façon, vous pouvez ajouter des attributs d’aide très dynamique et options de menu spécifiques à des projets imbriqués individuels.

10. La hiérarchie est générée pour l’affichage dans **l’Explorateur de solutions** avec un appel à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> (méthode).

     Vous transmettez la hiérarchie à l’environnement via `GetNestedHierarchy` pour générer la hiérarchie pour l’affichage dans l’Explorateur de solutions. De cette manière, la solution sait que le projet existe et peut être géré pour la création par le Gestionnaire de génération ou autorise les fichiers dans le projet pour être placés sous contrôle de code source.

11. Lorsque tous les projets imbriqués de Project1 ont été créés, le contrôle est passé à la solution et le processus est répété pour Project2.

     Ce même processus pour la création de projets imbriqués se produit pour un projet enfant qui a un enfant. Dans ce cas, si BuildProject1, qui est un enfant de Project1, avait des projets enfants, ils seront créés après BuildProject1 et avant (Projet2). Le processus est récursive et la hiérarchie est générée à partir du haut vers le bas.

     Quand un projet imbriqué est fermé, car l’utilisateur a fermé la solution ou spécifique au projet lui-même, l’autre méthode sur `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, est appelée. Le projet parent encapsule des appels à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> méthode avec le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> méthodes pour notifier des écouteurs aux événements de solution que les projets imbriqués sont en cours de fermeture.

Les rubriques suivantes traitent avec plusieurs autres concepts à prendre en compte lorsque vous implémentez les projets imbriqués :

- [Considérations pour décharger et recharger les projets imbriqués](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Prise en charge de l’Assistant pour les projets imbriqués](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Implémenter la gestion des commandes pour les projets imbriqués](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrer la boîte de dialogue AddItem pour les projets imbriqués](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Voir aussi

- [Ajouter des éléments à la boîte de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Inscrire les modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)
- [Liste de contrôle : Créer des types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Paramètres de contexte](../../extensibility/internals/context-parameters.md)
- [Fichier de l’Assistant (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)