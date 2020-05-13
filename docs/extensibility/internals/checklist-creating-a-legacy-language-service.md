---
title: 'Liste de contrôle : Création d’un service de langue héritée (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11785dab63cbb6a95ab2d34c5edbfb4525ebf34c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709791"
---
# <a name="checklist-create-a-legacy-language-service"></a>Liste de contrôle : Créer un service linguistique hérité
La liste de contrôle suivante résume les mesures de base que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vous devez prendre afin de créer un service linguistique pour l’éditeur de base. Pour intégrer votre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]service linguistique dans , vous devez créer un évaluateur d’expression débogé. Pour plus d’informations, voir [Écrire un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) dans [l’extensibility Visual Studio debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="steps-to-create-a-language-service"></a>Étapes pour créer un service linguistique

1. Implémentez l'interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.

    - Dans votre VSPackage, <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implémentez l’interface pour fournir le service linguistique.

    - Mettre votre service linguistique à la disposition de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> l’environnement de développement intégré (IDE) dans votre mise en œuvre.

2. Implémenter l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> dans la classe principale de service linguistique.

     L’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> est le point de départ de l’interaction entre l’éditeur de base et le service linguistique.

### <a name="optional-features"></a>Fonctionnalités facultatives
 Les fonctionnalités suivantes sont facultatives et peuvent être implémentées dans n’importe quel ordre. Ces fonctionnalités augmentent la fonctionnalité de votre service linguistique.

- Mise en couleur de la syntaxe

  Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. Votre implémentation de cette interface si les informations de analyse pour retourner les informations de couleur appropriées.

  La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> renvoie l’interface. Une instance de colorise séparée est créée pour <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> chaque tampon de texte, de sorte que vous devez implémenter l’interface séparément. Pour plus d’informations, voir [Coloriage Syntax dans un service de langue hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).

- Fenêtre de code

  Implémenter l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> pour permettre au service linguistique de recevoir une notification du moment où une nouvelle fenêtre de code est créée.

  La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> renvoie l’interface. Le service linguistique peut alors ajouter une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>interface utilisateur spéciale à la fenêtre de code dans . Le service linguistique peut également effectuer n’importe quel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>traitement spécial, comme l’ajout d’un filtre de vue textuelle dans .

- Filtre de vue de texte

  Pour fournir l’achèvement de la déclaration IntelliSense dans un service linguistique, vous devez intercepter certaines des commandes que la vue de texte traiterait autrement. Pour intercepter ces commandes, remplissez les étapes suivantes :

  - Implémentez <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pour participer à la chaîne de commandement et gérer les commandes de l’éditeur.

  - Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> la méthode et <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> passez dans votre implémentation.

  - Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> la méthode lorsque vous vous détachez de la vue afin que ces commandes ne soient plus transmises à vous.

  Les commandes qui doivent être traitées dépendent des services qui sont fournis. Pour plus d’informations, voir commandes importantes pour les [filtres de service linguistique](../../extensibility/internals/important-commands-for-language-service-filters.md).

  > [!NOTE]
  > L’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> doit être implémentée sur le même objet que l’interface. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>

- Compléter automatiquement les instructions

  Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.

  Prendre en charge la commande <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>d’achèvement <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> l’instruction <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> (c’est-à-dire) et appeler la méthode dans l’interface, en passant l’interface. Pour plus d’informations, voir [l’achèvement de l’instruction dans un service linguistique hérité](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).

- Conseils de méthode

  Implémentez l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> pour fournir des données pour la fenêtre de pointe de méthode.

  Installez le filtre de vue de texte pour manipuler les commandes de manière appropriée, afin que vous sachiez quand afficher une fenêtre de pointe de données de méthode. Pour plus d’informations, voir [Paramètres Info dans un service linguistique hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).

- Marqueurs d’erreur

  Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.

  Créez les objets marqueurs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> d’erreur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> qui implémentent l’interface et appellent la méthode, en passant l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> de l’objet marqueur d’erreur.

  Typiquement, chaque marqueur d’erreur gère un élément dans la fenêtre de la liste de tâches.

- Éléments de liste de tâches

  Implémentez une <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> classe d’élément de tâche fournissant l’interface.

  Implémentez une <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> classe de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> fournisseur de tâches fournissant l’interface et l’interface.

  Implémentez une classe d’enumérateur de tâches fournissant l’interface. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems>

  Enregistrez le fournisseur de tâches <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> avec la méthode de la liste de tâches.

  Obtenez <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> l’interface en appelant le fournisseur de services <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>du service linguistique avec le service GUID .

  Créez des objets d’élément de tâche et appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> méthode dans l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> lorsqu’il y a des tâches nouvelles ou mises à jour.

- Commentez les éléments de tâche

  Utilisez <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> et l’interface pour obtenir les jetons de tâche de commentaire.

  Obtenir <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> une interface <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> du service.

  Obtenir <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> de la méthode.

  Implémentez l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> pour écouter les changements dans la liste des jetons.

- mode Plan

  Il existe plusieurs options pour soutenir la mise en ligne. Par exemple, vous pouvez prendre en charge la commande **Collapse to Definitions,** fournir des régions de contour contrôlées par l’éditeur ou prendre en charge les régions contrôlées par les clients. Pour plus d’informations, voir [Comment : Fournir un soutien de mise en ligne élargi dans un service linguistique hérité.](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

- Enregistrement du service linguistique

  Pour plus d’informations sur la façon d’enregistrer un service linguistique, consultez [Register a legacy language service](../../extensibility/internals/registering-a-legacy-language-service2.md) et Manage [VSPackages](../../extensibility/managing-vspackages.md).

- Aide sensible au contexte

  Fournir le contexte à l’éditeur de l’une des façons suivantes :

  - Fournir le contexte pour les <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> marqueurs de texte en implémentant l’interface.

  - Fournir tout le contexte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> utilisateur en implémentant l’interface.

## <a name="see-also"></a>Voir aussi
- [Développer un service linguistique hérité](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Écrire un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
