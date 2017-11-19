---
title: "Liste de vérification : Création d’un Service de langage hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c06d246f7467e19969075537f321061463d1755
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="checklist-creating-a-legacy-language-service"></a>Liste de vérification : Création d’un Service de langage hérité
La liste suivante résume les étapes de base que vous devez prendre afin de créer un service de langage pour la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] éditeur principal. Pour intégrer votre service de langage dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous devez créer un évaluateur d’expression de débogage. Pour plus d’informations, consultez [l’écriture d’un évaluateur d’Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) dans les [d’extensibilité du débogueur Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="steps-for-creating-a-language-service"></a>Étapes de création d’un Service de langage  
  
1.  Implémentez l'interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  
  
    -   Dans votre package Visual Studio, vous devez implémenter la <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface afin de fournir le service de langage.  
  
    -   Rendre votre service de langage disponibles pour l’environnement de développement intégré (IDE) dans votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implémentation.  
  
2.  Implémentez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface dans la classe de service de langue principale.  
  
     Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface est le point de départ de l’interaction entre l’éditeur principal et le service de langage.  
  
### <a name="optional-features"></a>Fonctionnalités facultatives  
 Les fonctionnalités suivantes sont facultatives et peuvent être implémentées dans n’importe quel ordre. Ces fonctionnalités augmentent les fonctionnalités de votre service de langage.  
  
-   Mise en couleur de la syntaxe  
  
     Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. Votre implémentation de cette interface doit l’analyseur pour retourner les informations de couleur appropriée.  
  
     Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> méthode retourne la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interface. Création d’une instance Coloriseur distinct pour chaque mémoire tampon de texte, vous devez implémenter la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> séparément de l’interface. Pour plus d’informations, consultez [coloration de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
-   Fenêtre Code  
  
     Implémentez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interface pour activer le service de langage recevoir une notification de la création d’une nouvelle fenêtre de code.  
  
     Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> méthode retourne la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interface. Le service de langage peut ajouter ensuite une interface utilisateur spéciale dans la fenêtre de code de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>. Le service de langage peut également effectuer tout traitement spécial, telles que l’ajout d’un filtre d’affichage de texte dans <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.  
  
-   Filtre d’affichage de texte  
  
     Pour fournir la saisie semi-automatique IntelliSense dans un service de langage, vous devez intercepter certaines commandes qui serait autrement en charge l’affichage de texte. Pour intercepter ces commandes, procédez comme suit :  
  
    -   Implémentez <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> devant être inclus dans les commande chaîne et le handle de commandes de l’éditeur.  
  
    -   Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> méthode et passer votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implémentation.  
  
    -   Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> méthode lorsque vous détachez à partir de la vue afin que ces commandes ne sont plus transmises pour vous.  
  
     Les commandes qui doivent être gérés dépendent des services fournis. Pour plus d’informations, consultez [commandes Important pour les filtres de Service de langage](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
    > [!NOTE]
    >  Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interface doit être implémentée sur le même objet que le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface.  
  
-   Compléter automatiquement les instructions  
  
     Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.  
  
     Prend en charge la commande de fin de l’instruction (autrement dit, <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>) et appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> méthode dans le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface, en passant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interface. Pour plus d’informations, consultez [saisie semi-automatique des instructions dans un Service de langage hérité](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
-   Conseils de méthode  
  
     Implémentez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interface pour fournir des données pour la fenêtre d’info-bulle de méthode.  
  
     Installez le filtre de vue de texte pour gérer les commandes de façon appropriée, afin que vous sachiez quand afficher une fenêtre d’info-bulle de données (méthode). Pour plus d’informations, consultez [informations sur les paramètres dans un Service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
-   Marques d’erreur  
  
     Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.  
  
     Créer des objets de marqueur qui implémentent l’erreur la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface et appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> méthode, en passant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface de l’objet de marqueur d’erreur.  
  
     Chaque marqueur de l’erreur gère en général un élément dans la fenêtre liste des tâches.  
  
-   Éléments de liste de tâches  
  
     Implémenter une classe d’élément de tâche fournissant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> interface.  
  
     Implémenter une classe de fournisseur de tâche fournissant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> interface et <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> interface.  
  
     Implémenter une classe d’énumérateur de tâche fournissant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> interface.  
  
     Inscrire le fournisseur de tâche avec la liste des tâches <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> (méthode).  
  
     Obtenir le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interface en appelant le fournisseur de service du service de langage avec le GUID du service <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>.  
  
     Créer des objets d’éléments de tâche et appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> méthode dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interface lorsqu’il existe des nouvelles ou mises à jour de tâches.  
  
-   Éléments de tâche de commentaire  
  
     Utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interface et <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interface pour obtenir des jetons de tâche de commentaire.  
  
     Obtenir un <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> de l’interface à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> service.  
  
     Obtenir le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> de l’interface à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> (méthode).  
  
     Implémentez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> interface pour écouter les modifications apportées à la liste des jetons.  
  
-   mode Plan  
  
     Il existe plusieurs options pour prendre en charge le mode plan. Par exemple, vous pouvez prendre en charge la **réduire aux définitions** de commandes, indiquez les régions en mode plan de contrôlés par l’éditeur ou prend en charge les régions de contrôlé par le client. Pour plus d’informations, consultez [Comment : fournir développé en mode plan prise en charge dans un Service de langage hérité](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
-   Enregistrement du service de langage  
  
     Pour plus d’informations sur la façon d’inscrire un service de langage, consultez [l’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service2.md) et [la gestion des VSPackages](../../extensibility/managing-vspackages.md).  
  
-   Aide contextuelle  
  
     Fournir le contexte à l’éditeur de l’une des manières suivantes :  
  
    -   Fournir le contexte pour les marqueurs de texte en implémentant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interface.  
  
 Fournir tout le contexte utilisateur en implémentant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un Service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [L’écriture d’un évaluateur d’Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)