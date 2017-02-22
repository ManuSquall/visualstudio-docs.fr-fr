---
title: "Liste de v&#233;rification&#160;: Cr&#233;ation d’un Service de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services de langage"
  - "services de langage de code natif"
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Liste de v&#233;rification&#160;: Cr&#233;ation d’un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La liste de vérification suivante résume les étapes de base que vous devez entrer à nouveau la commande pour créer un service de langage pour l'éditeur principal de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Pour intégrer votre service de langage dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous devez créer un évaluateur d'expression de débogage.  Pour plus d'informations, consultez [Écriture d'un évaluateur d'Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) dans [Extensibilité du débogueur de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## Étapes pour créer un service de langage  
  
1.  Implémenter l'interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  
  
    -   Dans votre VSPackage, implémentez l'interface d' <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> pour fournir le service de langage.  
  
    -   Rendez votre service de langage disponible à l'environnement \(IDE\) de développement intégré dans votre implémentation d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> .  
  
2.  Implémentez l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> dans la classe principale de service de langage.  
  
     L'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> est le point de départ d'interaction entre l'éditeur principal et le service de langage.  
  
### Fonctionnalités facultatives  
 Les fonctionnalités suivantes sont facultatives et peuvent être implémentées dans n'importe quel ordre.  Ces fonctionnalités augmentent la fonctionnalité de votre service de langage.  
  
-   coloration de syntaxe  
  
     Implémenter l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  Votre implémentation de cette interface si les informations d'analyseur retournent des informations sur la couleur appropriées.  
  
     La méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> retourne l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> .  Une instance séparée de coloriseur est créée pour chaque mémoire tampon de texte, vous devez implémenter l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> séparément.  Pour plus d'informations, consultez [Couleurs de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
-   fenêtre de code  
  
     Implémentez l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> pour permettre au service de langage pour recevoir la notification de lorsqu'une nouvelle fenêtre de code est créée.  
  
     La méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> retourne l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> .  Le service de langage peut ensuite ajouter l'une interface utilisateur spéciale à la fenêtre de code dans <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>.  Le service de langage peut également effectuer un traitement spécial, par exemple ajouter un filtre d'affichage de texte dans l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.  
  
-   filtre d'affichage de texte  
  
     Pour fournir la saisie semi\-automatique des instructions Intellisense dans un service de langage, vous devez désactiver certaines commandes que l'affichage de texte ' sinon.  Pour arrêter ces commandes, exécutez les étapes suivantes :  
  
    -   Implémentez <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de participer aux touches de modification de chaîne et de handle de commande.  
  
    -   Appelez la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> et passez votre implémentation d' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
    -   Appelez la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> lorsque vous détachez de la vue afin que ces commandes ne soient plus passées à vous.  
  
     Les commandes qui doivent être gérées dépendent des services fournis.  Pour plus d'informations, consultez [Commandes importantes pour les filtres de Service de langage](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
    > [!NOTE]
    >  l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> doit être implémentée sur le même objet que l'interface d' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
-   Saisie semi\-automatique des instructions  
  
     Implémenter l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.  
  
     Prend en charge la commande de saisie semi\-automatique des instructions \(autrement dit, <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>\) et appelez la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> dans l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> , en passant l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> .  Pour plus d'informations, consultez [Saisie semi\-automatique des instructions dans un Service de langage hérité](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
-   conseils de méthode  
  
     Implémentez l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> pour fournir des données pour la fenêtre de conseils de méthode.  
  
     Installez le filtre d'affichage de texte pour gérer les commandes correctement, afin que vous sachiez lorsque l'affichage d'une fenêtre de conseils de données de méthode.  Pour plus d'informations, consultez [Informations sur les paramètres dans un Service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
-   Marqueurs d'erreurs  
  
     Implémenter l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.  
  
     Créez les objets de marque d'erreurs qui implémentent l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> et appelez la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> , en passant l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> de l'objet de marque d'erreurs.  
  
     En général chaque point d'erreurs gère un élément dans la fenêtre liste des tâches.  
  
-   éléments de la liste des tâches  
  
     implémentez une classe de tâche fournissant l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> .  
  
     implémentez une classe de fournisseur de tâche fournissant l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> et l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> .  
  
     implémentez une classe d'énumérateur de tâche fournissant l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> .  
  
     Enregistrer le fournisseur de tâche avec la méthode de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> de la liste des tâches.  
  
     Obtenez l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> en appelant le fournisseur de services du service de langage avec le service GUID <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>.  
  
     Créez les objets de tâche et appelez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> dans l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> lorsqu'il existe de nouvelles ou mises à jour tâches.  
  
-   Commentaires  
  
     Utilisez l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> et l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> pour obtenir les jetons de commentaire.  
  
     obtenez une interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> du service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> .  
  
     obtenez l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> de la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> .  
  
     Implémentez l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> pour écouter les modifications dans la liste de jetons.  
  
-   Mode Plan  
  
     Il existe plusieurs options pour prendre en charge le mode Plan.  Par exemple, vous pouvez prendre en charge la commande de **Réduire aux définitions** , fournir les régions en mode Plan contrôlées par l'éditeur, ou pour prendre en charge les régions client\-contrôlées.  Pour plus d'informations, consultez [Comment : fournir une prise en charge étendue de plan dans un Service de langage hérité](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
-   Inscription de service de langage  
  
     Pour plus d'informations sur l'enregistrement d'un service de langage, consultez [L’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service2.md) et le [La gestion de packages VS](../../extensibility/managing-vspackages.md).  
  
-   aide contextuelle  
  
     Fournissez le contexte à l'éditeur de l'une des façons suivantes :  
  
    -   Fournissez le contexte pour les marqueurs de texte en implémentant l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> .  
  
 Fournissez tout le contexte d'utilisateur en implémentant l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> .  
  
## Voir aussi  
 [Développement d'un Service de langage](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Écriture d'un évaluateur d'Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)