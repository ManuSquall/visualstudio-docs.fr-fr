---
title: 'Liste de vérification : Création d’un Service de langage hérité | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26d76a7977588839b8a61e6293f84cbf62b0a6dd
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629194"
---
# <a name="checklist-create-a-legacy-language-service"></a>Liste de vérification : Créer un service de langage hérité
La liste de vérification suivante résume les étapes de base que vous devez prendre afin de créer un service de langage pour la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] éditeur principal. Pour intégrer votre service de langage dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous devez créer un évaluateur d’expression de débogage. Pour plus d’informations, consultez [écrire un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) dans le [extensibilité du débogueur Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="steps-to-create-a-language-service"></a>Étapes de création d’un service de langage

1.  Implémentez l'interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.

    -   Dans votre VSPackage, mettre en œuvre la <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface pour fournir le service de langage.

    -   Rendre votre service de langage disponibles pour l’environnement de développement intégré (IDE) dans votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implémentation.

2.  Implémentez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface dans la classe de service de langage principal.

     Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface est le point de départ de l’interaction entre l’éditeur principal et le service de langage.

### <a name="optional-features"></a>Fonctionnalités facultatives
 Les fonctionnalités suivantes sont facultatives et peuvent être implémentées dans n’importe quel ordre. Ces fonctionnalités augmentent les fonctionnalités de votre service de langage.

-   Mise en couleur de la syntaxe

     Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. Votre implémentation de cette interface doit les informations de l’analyseur pour retourner les informations de couleur appropriée.

     Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> méthode retourne le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interface. Une instance de Coloriseur distincte est créée pour chaque mémoire tampon de texte, vous devez implémenter le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> séparément de l’interface. Pour plus d’informations, consultez [couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).

-   Fenêtre Code

     Implémentez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interface pour activer le service de langage recevoir une notification de création d’une nouvelle fenêtre de code.

     Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> méthode retourne le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interface. Le service de langage peut ajouter ensuite une interface utilisateur spéciale dans la fenêtre de code de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>. Le service de langage peut également effectuer tout traitement spécial, telles que l’ajout d’un filtre de vue de texte dans <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.

-   Filtre d’affichage de texte

     Pour fournir la saisie semi-automatique des instructions IntelliSense dans un service de langage, vous devez intercepter certaines commandes qui prendrait autrement en charge l’affichage de texte. Pour intercepter ces commandes, procédez comme suit :

    -   Implémentez <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> à participer aux commande chaîne et la poignée de commandes de l’éditeur.

    -   Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> (méthode) et passez votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implémentation.

    -   Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> méthode lorsque vous détachez à partir de la vue afin que ces commandes ne sont plus transmises à vous.

    Les commandes qui doivent être gérés dépendent des services qui sont fournis. Pour plus d’informations, consultez [commandes importantes pour le langage de service filtres](../../extensibility/internals/important-commands-for-language-service-filters.md).

    > [!NOTE]
    >  Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interface doit être implémentée sur le même objet que le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface.

-   Compléter automatiquement les instructions

     Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.

     Prend en charge de la commande de saisie semi-automatique d’instruction (autrement dit, <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>) et appeler le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> méthode dans le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface, en passant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interface. Pour plus d’informations, consultez [saisie semi-automatique des instructions dans un service de langage hérité](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).

-   Conseils de méthode

     Implémentez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interface pour fournir des données pour la fenêtre d’info-bulle de méthode.

     Installez le filtre d’affichage de texte pour gérer les commandes de manière appropriée, afin que vous sachiez quand afficher une fenêtre d’info-bulle de données (méthode). Pour plus d’informations, consultez [informations sur les paramètres dans un service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).

-   Marqueurs d’erreur

     Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.

     Créer des objets de marqueur qui implémentent l’erreur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface et appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> méthode, en passant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface de l’objet de marqueur d’erreur.

     Chaque marqueur de l’erreur gère habituellement un élément dans la fenêtre liste des tâches.

-   Éléments de liste de tâches

     Implémenter une classe d’élément de tâche fournissant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> interface.

     Implémenter une classe de fournisseur de tâche fournissant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> interface et le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> interface.

     Implémenter une classe d’énumérateur de tâche fournissant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> interface.

     Inscrire le fournisseur de tâche avec la liste des tâches <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> (méthode).

     Obtenir le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interface en appelant le fournisseur de service du service de langage avec le GUID du service <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>.

     Créer des objets d’élément de tâche et appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> méthode dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interface en cas de nouveau ou mis à jour de tâches.

-   Éléments de tâche de commentaire

     Utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interface et le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interface pour obtenir des jetons de tâche de commentaire.

     Obtenir un <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> de l’interface à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> service.

     Obtenir le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> de l’interface à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> (méthode).

     Implémentez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> interface pour écouter les modifications dans la liste des jetons.

-   mode Plan

     Il existe plusieurs options pour prendre en charge le mode plan. Par exemple, vous pouvez prendre en charge la **réduire aux définitions** commande, indiquez les régions en mode de plan contrôlés par l’éditeur ou prennent en charge les régions contrôlé par le client. Pour plus d'informations, voir [Procédure : Fournir une prise en charge étendue de mode plan dans un service de langage hérité](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).

-   Inscription du service de langage

     Pour plus d’informations sur l’inscription d’un service de langage, consultez [inscrire un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service2.md) et [gérer les VSPackages](../../extensibility/managing-vspackages.md).

-   Aide contextuelle

     Fournir le contexte à l’éditeur de l’une des manières suivantes :

    -   Fournissent un contexte pour les marqueurs de texte en implémentant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interface.

    -   Fournir tout le contexte utilisateur en implémentant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interface.

## <a name="see-also"></a>Voir aussi
- [Développer un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Écrire un évaluateur d’expression de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)