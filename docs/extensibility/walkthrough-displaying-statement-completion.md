---
title: "Proc&#233;dure pas &#224; pas : Affichage de saisie semi-automatique des instructions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), nouvelles - saisie semi-automatique des instructions"
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 36
---
# Proc&#233;dure pas &#224; pas : Affichage de saisie semi-automatique des instructions
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez implémenter la saisie semi\-automatique des instructions en langage en définissant les identificateurs pour lequel vous souhaitez fournir l'achèvement et de déclenchement ensuite une session de saisie semi\-automatique. Vous pouvez définir la saisie semi\-automatique des instructions dans le contexte d'un service de langage, définir votre propre extension de nom de fichier et le type de contenu et afficher achèvement de ce type, ou vous pouvez déclencher la saisie semi\-automatique pour un type de contenu existant, par exemple, « clair ». Cette procédure pas à pas montre comment déclencher la saisie semi\-automatique des instructions pour le type de contenu « texte brut », qui est le type de contenu des fichiers texte. Le type de contenu « texte » est l'ancêtre de tous les autres types de contenu, y compris le code et les fichiers XML.  
  
 Saisie semi\-automatique des instructions est généralement déclenché en tapant certains caractères, par exemple, en tapant le début d'un identificateur, tel que « using ». Il est généralement fermée en appuyant sur la touche espace, une tabulation ou entrée pour valider une sélection. Vous pouvez implémenter les fonctionnalités IntelliSense qui sont déclenchées par la saisie d'un caractère à l'aide d'un gestionnaire de commandes pour les séquences de touches \(la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface\) et un fournisseur de gestionnaire qui implémente le <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interface. Pour créer la source de saisie semi\-automatique, qui est la liste des identificateurs qui participent à saisie semi\-automatique, implémentez le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> interface et un fournisseur de source de saisie semi\-automatique \(le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> interface\). Les fournisseurs sont des composants de Managed Extensibility Framework \(MEF\). Ils sont chargés d'exportation les classes source et le contrôleur et l'importation des services et des courtiers — par exemple, le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, qui permet la navigation dans la mémoire tampon de texte et la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, qui déclenche la session de saisie semi\-automatique.  
  
 Cette procédure pas à pas montre comment implémenter la saisie semi\-automatique des instructions pour un jeu codé en dur des identificateurs. Dans les implémentations complètes, le service de langage et de la documentation de langage sont chargés de fournir ce contenu.  
  
## Composants requis  
 À partir de Visual Studio 2015, vous n'installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d'installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Création d'un projet MEF  
  
#### Pour créer un projet MEF  
  
1.  Créez un projet VSIX c\#. \(Dans le **Nouveau projet** boîte de dialogue, sélectionnez **Visual C\# \/ extensibilité**, puis **projet VSIX**.\) Nommez la solution `CompletionTest`.  
  
2.  Ajouter un modèle d'élément éditeur classifieur au projet. Pour plus d'informations, consultez [Création d'une Extension avec un éditeur de modèle d'élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
4.  Ajoutez les références suivantes au projet et assurez\-vous que **CopyLocal** est défini sur `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Assemblys Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## L'implémentation de la Source de saisie semi\-automatique  
 La source de saisie semi\-automatique est responsable de la collecte de l'ensemble des identificateurs et ajouter le contenu de la fenêtre de saisie semi\-automatique lorsqu'un utilisateur tape un déclencheur d'achèvement, telles que les premières lettres d'un identificateur. Dans cet exemple, les identificateurs et leurs descriptions sont codées en dur dans le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> \(méthode\). Dans la plupart des utilisations réelles, vous utiliseriez Analyseur de votre langage pour obtenir les jetons pour remplir la liste de saisie semi\-automatique.  
  
#### Pour implémenter la source de saisie semi\-automatique  
  
1.  Ajoutez un fichier de classe et nommez\-le `TestCompletionSource`.  
  
2.  Ajoutez les importations :  
  
     [!code-cs[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  Modifiez la déclaration de classe pour `TestCompletionSource` afin qu'elle implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-cs[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  Ajouter des champs privés pour le fournisseur de code source, la mémoire tampon de texte et une liste de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> objets \(qui correspondent aux identificateurs qui participeront à la session de saisie semi\-automatique\) :  
  
     [!code-cs[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  Ajoutez un constructeur qui définit le fournisseur de source et de la mémoire tampon. La `TestCompletionSourceProvider` classe est définie dans les étapes suivantes :  
  
     [!code-cs[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> méthode en ajoutant un jeu de saisie semi\-automatique qui contient les saisies semi\-automatiques que vous souhaitez fournir dans le contexte. Chaque jeu de saisie semi\-automatique contient un ensemble de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> et abouties et correspond à un onglet de la fenêtre de saisie semi\-automatique. \(Dans les projets Visual Basic, les onglets de la fenêtre exécution sont nommés **commune** et **tous les**.\) La méthode FindTokenSpanAtPosition est définie à l'étape suivante.  
  
     [!code-cs[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  La méthode suivante est utilisée pour rechercher le mot en cours à partir de la position du curseur :  
  
     [!code-cs[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  Implémentez la `Dispose()` méthode :  
  
     [!code-cs[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## Implémentation du fournisseur de Source de saisie semi\-automatique  
 Le fournisseur de source de saisie semi\-automatique est le composant MEF qui instancie la source de saisie semi\-automatique.  
  
#### Pour implémenter le fournisseur de source de saisie semi\-automatique  
  
1.  Ajoutez une classe nommée `TestCompletionSourceProvider` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Exporter cette classe avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « clair » et un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de « fin de test ».  
  
     [!code-cs[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  Importer un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, qui est utilisé pour rechercher le mot actuel dans la source de saisie semi\-automatique.  
  
     [!code-cs[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> méthode pour instancier la source de saisie semi\-automatique.  
  
     [!code-cs[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## Implémentation du fournisseur de gestionnaire de commande de fin  
 Le fournisseur de gestionnaire de commandes de saisie semi\-automatique est dérivé d'un <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, qui écoute un événement de création de vue de texte et convertit la vue d'un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>qui permet l'ajout de la commande à la chaîne de commande de l'interpréteur de commandes de Visual Studio, à un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Étant donné que cette classe est une exportation MEF, vous pouvez l'utiliser également pour importer les services requis par le Gestionnaire de la commande.  
  
#### Pour implémenter le fournisseur de gestionnaire de commandes de saisie semi\-automatique  
  
1.  Ajoutez un fichier nommé `TestCompletionCommandHandler`.  
  
2.  Ajoutez ces instructions using :  
  
     [!code-cs[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  Ajoutez une classe nommée `TestCompletionHandlerProvider` qui implémente <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Exporter cette classe avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> du « Gestionnaire d'achèvement jeton », un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « clair » et un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-cs[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  Importer le <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, qui permet la conversion d'un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> à un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, un <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, et un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> qui permet l'accès aux services de Visual Studio standards.  
  
     [!code-cs[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  Implémentez la <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> méthode pour instancier le Gestionnaire de commandes.  
  
     [!code-cs[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## Implémentation du Gestionnaire de commandes de saisie semi\-automatique  
 Étant donné que la saisie semi\-automatique des instructions est déclenchée par les séquences de touches, vous devez implémenter le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface pour recevoir et traiter les séquences de touches qui déclenchent, valident et fermer la session de saisie semi\-automatique.  
  
#### Pour implémenter le Gestionnaire de commandes de saisie semi\-automatique  
  
1.  Ajoutez une classe nommée `TestCompletionCommandHandler` qui implémente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
     [!code-cs[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
     [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2.  Ajouter des champs privés pour le Gestionnaire de commande suivant \(à laquelle vous passez la commande\), l'affichage de texte, le fournisseur du Gestionnaire de commandes \(ce qui permet d'accéder à divers services\) et une session de saisie semi\-automatique :  
  
     [!code-cs[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
     [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3.  Ajoutez un constructeur qui définit l'affichage de texte et les champs du fournisseur et ajoute la commande à la chaîne de commande :  
  
     [!code-cs[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
     [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4.  Implémentez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode en passant la commande le long :  
  
     [!code-cs[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
     [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5.  Implémentez la méthode <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Lorsque cette méthode reçoit une séquence de touches, il doit faire un des éléments suivants :  
  
    -   Autoriser le caractère à écrire dans la mémoire tampon et puis déclencher ou filtrer la saisie semi\-automatique. \(Les caractères imprimables communiquent.\)  
  
    -   Valider l'achèvement, mais n'autorisent pas le caractère à écrire dans la mémoire tampon. \(Un espace blanc, Tab et entrée faire lorsqu'une session de saisie semi\-automatique s'affiche.\)  
  
    -   Permet la commande à passer au gestionnaire suivant. \(Toutes les autres commandes.\)  
  
     Étant donné que cette méthode peut afficher l'interface utilisateur, appelez <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> pour vous assurer qu'elle n'est pas appelée dans un contexte d'automation :  
  
     [!code-cs[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6.  Ce code est une méthode privée qui déclenche la session de saisie semi\-automatique :  
  
     [!code-cs[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
     [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7.  L'exemple suivant est une méthode privée qui annule l'abonnement le <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> événement :  
  
     [!code-cs[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
     [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## Création et test du code  
 Pour tester ce code, générez la solution CompletionTest et exécutez\-le dans l'instance expérimentale.  
  
#### Pour générer et tester la solution CompletionTest  
  
1.  Générez la solution.  
  
2.  Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
3.  Créez un fichier texte et tapez du texte qui inclut le mot « ajouter ».  
  
4.  Lorsque vous tapez tout d'abord « a » et ensuite « d », une liste qui contient « addition » et « adaptation » doit être affichée. Notez que l'addition est sélectionnée. Lorsque vous tapez un autre « d », la liste doit contenir uniquement « Ajout », qui est maintenant activée. Vous pouvez valider « addition » en appuyant sur la touche espace, une tabulation ou entrée, ou fermer la liste en tapant ÉCHAP ou une autre touche.  
  
## Voir aussi  
 [Procédure pas à pas : Liaison d'un Type de contenu à une Extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)