---
title: 'Liste de vérification : création d’un service de langage hérité | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b79afe64aafac473d4fe5d22464998d0c2f0537
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840070"
---
# <a name="checklist-creating-a-legacy-language-service"></a>Checklist : création d’un service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La liste de vérification suivante résume les étapes de base que vous devez suivre pour créer un service de langage pour l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] éditeur principal. Pour intégrer votre service de langage dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , vous devez créer un évaluateur d’expression de débogage. Pour plus d’informations, consultez [écriture d’un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) dans l' [extensibilité du débogueur Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="steps-for-creating-a-language-service"></a>Étapes de création d’un service de langage  
  
1. Implémentez l'interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  
  
    - Dans votre VSPackage, implémentez l' <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface pour fournir le service de langage.  
  
    - Rendez votre service de langage accessible à l’environnement de développement intégré (IDE) dans votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implémentation.  
  
2. Implémentez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface dans la classe de service de langage principale.  
  
     L' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface est le point de départ de l’interaction entre l’éditeur de base et le service de langage.  
  
### <a name="optional-features"></a>Fonctionnalités facultatives  
 Les fonctionnalités suivantes sont facultatives et peuvent être implémentées dans n’importe quel ordre. Ces fonctionnalités augmentent les fonctionnalités de votre service de langage.  
  
- Mise en couleur de la syntaxe  
  
   Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. Votre implémentation de cette interface doit les informations de l’analyseur pour retourner les informations de couleur appropriées.  
  
   La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> méthode retourne l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interface. Une instance Coloriseur distincte est créée pour chaque mémoire tampon de texte. vous devez donc implémenter l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interface séparément. Pour plus d’informations, consultez [coloration de la syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
- Fenêtre de code  
  
   Implémentez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interface pour permettre au service de langage de recevoir une notification lors de la création d’une nouvelle fenêtre de code.  
  
   La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> méthode retourne l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interface. Le service de langage peut ensuite ajouter une interface utilisateur spéciale à la fenêtre de code dans <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> . Le service de langage peut également effectuer tout traitement spécial, tel que l’ajout d’un filtre d’affichage de texte dans <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A> .  
  
- Filtre d’affichage de texte  
  
   Pour fournir la saisie semi-automatique des instructions IntelliSense dans un service de langage, vous devez intercepter certaines des commandes que l’affichage de texte gérerait autrement. Pour intercepter ces commandes, procédez comme suit :  
  
  - Implémentez <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pour participer à la chaîne de commande et gérer les commandes de l’éditeur.  
  
  - Appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> méthode et transmettez votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implémentation.  
  
  - Appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> méthode lorsque vous détachez de la vue afin que ces commandes ne vous soient plus passées.  
  
    Les commandes qui doivent être gérées dépendent des services fournis. Pour plus d’informations, consultez [commandes importantes pour les filtres du service de langage](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
  > [!NOTE]
  > L' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interface doit être implémentée sur le même objet que l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface.  
  
- Compléter automatiquement les instructions  
  
   Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.  
  
   Prenez en charge la commande de saisie semi-automatique des instructions (c’est-à-dire <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> ) et appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> méthode dans l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface, en passant l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interface. Pour plus d’informations, consultez [saisie semi-automatique des instructions dans un service de langage hérité](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
- Conseils de méthode  
  
   Implémentez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interface pour fournir des données pour la fenêtre d’info-bulle de méthode.  
  
   Installez le filtre d’affichage de texte pour gérer les commandes de manière appropriée, afin de savoir quand afficher une fenêtre d’info-bulle de données de méthode. Pour plus d’informations, consultez informations sur les [paramètres dans un service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
- Marqueurs d’erreur  
  
   Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.  
  
   Créez les objets du marqueur d’erreur qui implémentent l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface et appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> méthode, en passant l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface de l’objet du marqueur d’erreur.  
  
   En général, chaque marqueur d’erreur gère un élément dans la fenêtre Liste des tâches.  
  
- Éléments de Liste des tâches  
  
   Implémentez une classe d’élément de tâche fournissant l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> interface.  
  
   Implémentez une classe de fournisseur de tâche qui fournit l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> interface et l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> interface.  
  
   Implémentez une classe d’énumérateur de tâche fournissant l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> interface.  
  
   Inscrivez le fournisseur de tâche avec la méthode de la liste de tâches <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> .  
  
   Obtenez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interface en appelant le fournisseur de services du service de langage avec le GUID du service <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> .  
  
   Créez des objets d’élément de tâche et appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> méthode dans l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interface lorsqu’il existe des tâches nouvelles ou mises à jour.  
  
- Éléments de tâche de commentaire  
  
   Utilisez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interface et l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interface pour obtenir les jetons de tâche de commentaire.  
  
   Obtenez une <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interface à partir du <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> service.  
  
   Obtenez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interface à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> méthode.  
  
   Implémentez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> interface pour écouter les modifications dans la liste des jetons.  
  
- mode Plan  
  
   Il existe plusieurs options pour la prise en charge du mode plan. Par exemple, vous pouvez prendre en charge la commande **réduire aux définitions** , fournir des régions de plan contrôlées par l’éditeur ou prendre en charge les régions contrôlées par le client. Pour plus d’informations, consultez Guide pratique [pour fournir une prise en charge développée du mode plan dans un service de langage hérité](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
- Inscription du service de langage  
  
   Pour plus d’informations sur l’inscription d’un service de langage, consultez [inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service2.md) et [gestion des VSPackages](../../extensibility/managing-vspackages.md).  
  
- Aide contextuelle  
  
   Fournissez un contexte à l’éditeur de l’une des manières suivantes :  
  
  - Fournissez le contexte des marqueurs de texte en implémentant l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interface.  
  
  Fournissez tout le contexte utilisateur en implémentant l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Écriture d’un évaluateur d’expression de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
