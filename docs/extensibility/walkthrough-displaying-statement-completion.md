---
title: "Procédure pas à pas : Affichage de saisie semi-automatique des instructions | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d9c3b44bd46c34a864896cbf1002505085be5143
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-displaying-statement-completion"></a>Procédure pas à pas : Affichage de saisie semi-automatique des instructions
Vous pouvez implémenter basée sur le langage de saisie semi-automatique des instructions en définissant les identificateurs pour lequel vous souhaitez fournir la saisie semi-automatique et de déclenchement puis d’une session de saisie semi-automatique. Vous pouvez définir la saisie semi-automatique des instructions dans le contexte d’un service de langage, définissez votre propre extension de nom de fichier et le type de contenu et ensuite afficher la saisie semi-automatique pour uniquement ce type, ou vous pouvez déclencher la saisie semi-automatique pour un type de contenu existant, par exemple, « texte en clair ». Cette procédure pas à pas montre comment déclencher la saisie semi-automatique des instructions pour le type de contenu « texte en clair », qui est le type de contenu des fichiers texte. Le type de contenu « text » est l’ancêtre de tous les autres types de contenu, y compris le code et les fichiers XML.  
  
 Saisie semi-automatique des instructions sont généralement déclenchée en tapant certains caractères, par exemple, en tapant le début d’un identificateur, tel que « using ». En règle générale, il disparaît en appuyant sur la touche espace, tabulation ou entrée pour valider une sélection. Vous pouvez implémenter les fonctionnalités IntelliSense qui sont déclenchées par la saisie d’un caractère à l’aide d’un gestionnaire de commandes pour les séquences de touches (la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface) et un fournisseur gestionnaire qui implémente le <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interface. Pour créer la source de saisie semi-automatique, qui est la liste des identificateurs qui participent de saisie semi-automatique, implémentez le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> interface et un fournisseur de source de saisie semi-automatique (le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> interface). Les fournisseurs sont des composants de Managed Extensibility Framework (MEF). Dont il est responsable de l’exportation les classes source et le contrôleur et l’importation des services et aux courtiers : par exemple, le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, ce qui permet la navigation dans la mémoire tampon de texte et le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, ce qui déclenche la session de saisie semi-automatique.  
  
 Cette procédure pas à pas montre comment implémenter la saisie semi-automatique des instructions pour un jeu codé en dur des identificateurs. Dans les implémentations complètes, le service de langage et de la documentation de langage sont chargés de fournir ce contenu.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Création d’un projet MEF  
  
#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF  
  
1.  Créez un projet VSIX c#. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual c# / extensibilité**, puis **projet VSIX**.) Nommez la solution `CompletionTest`.  
  
2.  Ajouter un modèle d’élément classifieur d’éditeur pour le projet. Pour plus d’informations, consultez [création d’une Extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
4.  Ajoutez les références suivantes au projet et vous assurer que **CopyLocal** a la valeur `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Assemblys Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-the-completion-source"></a>Implémentation de la Source de saisie semi-automatique  
 La source de saisie semi-automatique est responsable de la collecte de l’ensemble des identificateurs et ajouter le contenu de la fenêtre de saisie semi-automatique lorsqu’un utilisateur tape un déclencheur d’achèvement, telles que les premières lettres d’un identificateur. Dans cet exemple, les identificateurs et leurs descriptions sont codés en dur dans le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> (méthode). Dans la plupart des utilisations du monde réel, vous utiliseriez Analyseur de votre langage pour obtenir les jetons pour remplir la liste de saisie semi-automatique.  
  
#### <a name="to-implement-the-completion-source"></a>Pour implémenter la source de saisie semi-automatique  
  
1.  Ajoutez un fichier de classe et nommez-le `TestCompletionSource`.  
  
2.  Ajoutez ces importations :  
  
     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  Modifiez la déclaration de classe pour `TestCompletionSource` afin qu’elle implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  Ajoutez des champs privés pour le fournisseur de code source, la mémoire tampon de texte et une liste de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> objets (qui correspondent aux identificateurs qui participeront à la session de saisie semi-automatique) :  
  
     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  Ajoutez un constructeur qui définit le fournisseur de source et de la mémoire tampon. La `TestCompletionSourceProvider` classe est définie dans les étapes suivantes :  
  
     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> méthode en ajoutant un jeu de saisie semi-automatique qui contient les saisies semi-automatiques que vous souhaitez fournir dans le contexte. Chaque jeu de saisie semi-automatique contient un jeu de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> réussies et correspond à un onglet de la fenêtre de saisie semi-automatique. (Dans les projets Visual Basic, les onglets de fenêtre de saisie semi-automatique sont nommés **commune** et **tous les**.) La méthode FindTokenSpanAtPosition est définie dans l’étape suivante.  
  
     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  La méthode suivante est utilisée pour rechercher le mot actuel à partir de la position du curseur :  
  
     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  Implémentez la `Dispose()` méthode :  
  
     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## <a name="implementing-the-completion-source-provider"></a>Implémentation du fournisseur de Source de saisie semi-automatique  
 Le fournisseur de source de saisie semi-automatique est la partie du composant MEF qui instancie la source de saisie semi-automatique.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Pour implémenter le fournisseur de source de saisie semi-automatique  
  
1.  Ajoutez une classe nommée `TestCompletionSourceProvider` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Exporter cette classe avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « texte en clair » et un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de « exécution de test ».  
  
     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  Importer un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, qui est utilisé pour rechercher le mot actuel dans la source de saisie semi-automatique.  
  
     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> méthode pour instancier la source de saisie semi-automatique.  
  
     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Implémentation du fournisseur de gestionnaire de commande de fin  
 Le fournisseur de gestionnaire de commandes de saisie semi-automatique est dérivé d’un <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, qui écoute un événement de création de vue de texte et convertit la vue à partir une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, ce qui permet l’ajout de la commande à la chaîne de commande de l’interpréteur de commandes de Visual Studio : à un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Étant donné que cette classe est une exportation MEF, vous pouvez l’utiliser également pour importer les services requis par le Gestionnaire de commande proprement dit.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Pour implémenter le fournisseur de gestionnaire de commande de fin  
  
1.  Ajoutez un fichier nommé `TestCompletionCommandHandler`.  
  
2.  Ajoutez ces instructions using :  
  
     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  Ajoutez une classe nommée `TestCompletionHandlerProvider` qui implémente <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Exporter cette classe avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> du « Gestionnaire de jeton d’achèvement », un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « texte en clair » et un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  Importer le <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, qui permet la conversion d’un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> à un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, un <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>et un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> qui permet d’accéder aux services de Visual Studio standard.  
  
     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  Implémentez la <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> méthode pour instancier le Gestionnaire de commandes.  
  
     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## <a name="implementing-the-completion-command-handler"></a>Implémentation du Gestionnaire de commande de fin  
 Étant donné que la saisie semi-automatique des instructions sont déclenchée par les séquences de touches, vous devez implémenter la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface pour recevoir et traiter les séquences de touches qui déclenchent, valident et fermer la session de saisie semi-automatique.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Pour implémenter le Gestionnaire de commandes de saisie semi-automatique  
  
1.  Ajoutez une classe nommée `TestCompletionCommandHandler` qui implémente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
     [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
     [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2.  Ajoutez des champs privés pour le Gestionnaire de commandes suivant (à laquelle vous passez la commande), l’affichage de texte, le fournisseur du Gestionnaire de commandes (ce qui permet d’accéder à divers services) et une session de saisie semi-automatique :  
  
     [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
     [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3.  Ajoutez un constructeur qui définit l’affichage de texte et les champs du fournisseur et ajoute la commande à la chaîne de commande :  
  
     [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
     [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4.  Implémentez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode en passant la commande le long de :  
  
     [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
     [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5.  Implémentez la méthode <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Lorsque cette méthode reçoit une séquence de touches, il effectuez l’une des opérations suivantes :  
  
    -   Autoriser le caractère à écrire dans la mémoire tampon et puis déclenche ou filtrer la saisie semi-automatique. (Les caractères imprimables cette opération).  
  
    -   Valider l’achèvement, mais n’autorisent pas le caractère à écrire dans la mémoire tampon. (Un espace blanc, Tab et entrée cette opération lorsqu’une session de saisie semi-automatique est affichée).  
  
    -   Autoriser la commande pour être transmises au gestionnaire suivant. (Toutes les autres commandes.)  
  
     Étant donné que cette méthode peut afficher l’interface utilisateur, appelez <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> pour vous assurer qu’elle n’est pas appelée dans un contexte d’automation :  
  
     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6.  Ce code est une méthode privée qui déclenche la session de saisie semi-automatique :  
  
     [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
     [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7.  L’exemple suivant est une méthode privée qui annule l’abonnement à partir de la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> événement :  
  
     [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
     [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
 Pour tester ce code, générez la solution CompletionTest et l’exécuter dans l’instance expérimentale.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Pour générer et tester la solution CompletionTest  
  
1.  Générez la solution.  
  
2.  Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
3.  Créez un fichier texte et tapez du texte qui inclut le mot « ajouter ».  
  
4.  Lorsque vous tapez tout d’abord « a » et ensuite « d », une liste qui contient « addition » et « adaptation » doit être affichée. Notez que l’addition est sélectionnée. Lorsque vous tapez un autre « d », la liste doit contenir uniquement « Ajout », qui est maintenant sélectionnée. Vous pouvez valider « addition » en appuyant sur la touche espace, tabulation ou entrée, ou fermer la liste en tapant ÉCHAP ou une autre clé.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Liaison d’un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)