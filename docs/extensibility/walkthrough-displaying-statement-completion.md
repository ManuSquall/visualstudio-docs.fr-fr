---
title: 'Procédure pas à pas : Affichage de saisie semi-automatique des instructions | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f117209c8e1d57c64ab53df608fe55ae27f0cff0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312405"
---
# <a name="walkthrough-display-statement-completion"></a>Procédure pas à pas : Afficher la saisie semi-automatique des instructions
Vous pouvez implémenter la saisie semi-automatique des instructions en langage en définissant les identificateurs pour lequel vous souhaitez fournir la saisie semi-automatique et puis déclenchant une session de saisie semi-automatique. Vous pouvez définir la saisie semi-automatique des instructions dans le contexte d’un service de langage, définir votre propre extension de nom de fichier et le type de contenu, puis affichez saisie semi-automatique pour uniquement ce type. Ou, vous pouvez déclencher la saisie semi-automatique pour un type de contenu existant, par exemple, « texte en clair ». Cette procédure pas à pas montre comment déclencher la saisie semi-automatique des instructions pour le type de contenu « texte en clair », qui est le type de contenu des fichiers texte. Le type de contenu « texte » est l’ancêtre de tous les autres types de contenu, y compris le code et les fichiers XML.

 Saisie semi-automatique des instructions sont généralement déclenchées en tapant certains caractères, par exemple, en tapant le début d’un identificateur, tel que « using ». Il est généralement ignorée en appuyant sur la **espace**, **onglet**, ou **entrée** clé pour valider une sélection. Vous pouvez implémenter les fonctionnalités IntelliSense qui déclenchent lors de la saisie d’un caractère à l’aide d’un gestionnaire de commandes pour les séquences de touches (la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface) et un fournisseur de gestionnaire qui implémente le <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interface. Pour créer la source d’achèvement, qui est la liste des identificateurs qui participent à saisie semi-automatique, implémentez le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> interface et un fournisseur de source de saisie semi-automatique (le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> interface). Les fournisseurs sont des composants de Managed Extensibility Framework (MEF). Ils ont la charge pour exporter les classes source et de contrôleur et importer des services et des courtiers — par exemple, le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, qui permet la navigation dans la mémoire tampon de texte et le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, qui déclenche la session de saisie semi-automatique.

 Cette procédure pas à pas montre comment implémenter la saisie semi-automatique des instructions pour un ensemble codées en dur des identificateurs. Dans les implémentations complètes, le service de langage et de la documentation du langage sont chargés de fournir ce contenu.

## <a name="prerequisites"></a>Prérequis
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Créer un projet MEF

#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF

1. Créez un projet c# VSIX. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual c# / extensibilité**, puis **projet VSIX**.) Nommez la solution `CompletionTest`.

2. Ajouter un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [créer une extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

4. Ajoutez les références suivantes au projet et assurez-vous que l’option **CopyLocal** est défini sur `false`:

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.14.0

     Microsoft.VisualStudio.Shell.Immutable.10.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-the-completion-source"></a>Implémenter la source d’achèvement
 La source d’achèvement est responsable de la collecte de l’ensemble des identificateurs et en ajoutant le contenu dans la fenêtre de saisie semi-automatique lorsqu’un utilisateur tape un déclencheur d’achèvement, telles que les premières lettres d’un identificateur. Dans cet exemple, les identificateurs et leurs descriptions sont codées en dur dans le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> (méthode). Dans la plupart des utilisations du monde réel, vous utiliseriez Analyseur de votre langage pour obtenir les jetons pour remplir la liste de saisie semi-automatique.

### <a name="to-implement-the-completion-source"></a>Pour implémenter la source d’achèvement

1. Ajoutez un fichier de classe et nommez-le `TestCompletionSource`.

2. Ajoutez ces importations :

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. Modifiez la déclaration de classe pour `TestCompletionSource` afin qu’elle implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Ajouter des champs privés pour le fournisseur de code source, la mémoire tampon de texte et une liste de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> objets (qui correspondent aux identificateurs qui participeront à la session de saisie semi-automatique) :

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Ajoutez un constructeur qui définit le fournisseur de code source et de la mémoire tampon. Le `TestCompletionSourceProvider` classe est définie dans les étapes ultérieures :

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> méthode en ajoutant un jeu de saisies semi-automatiques qui contient les saisies semi-automatiques que vous souhaitez fournir dans le contexte. Chaque jeu de saisies semi-automatiques contient un ensemble de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> saisies semi-automatiques et correspond à un onglet de la fenêtre de saisie semi-automatique. (Dans les projets Visual Basic, les onglets de fenêtre de saisie semi-automatique sont nommés **commune** et **tous les**.) La méthode `FindTokenSpanAtPosition` est définie à l'étape suivante.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. La méthode suivante est utilisée pour rechercher le mot actuel à partir de la position du curseur :

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. Implémentez la `Dispose()` méthode :

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Implémenter le fournisseur de source de saisie semi-automatique
 Le fournisseur de source de saisie semi-automatique est la partie du composant MEF qui instancie la source d’achèvement.

### <a name="to-implement-the-completion-source-provider"></a>Pour implémenter le fournisseur de source de saisie semi-automatique

1. Ajoutez une classe nommée `TestCompletionSourceProvider` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Exporter cette classe avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « texte en clair » et un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de « exécution de test ».

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. Importer un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, qui recherche le mot actuel dans la source d’achèvement.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> méthode pour instancier la source d’achèvement.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Implémenter le fournisseur de gestionnaire de commandes de saisie semi-automatique
 Le fournisseur de gestionnaire de commandes de saisie semi-automatique est dérivé d’un <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, qui écoute un événement de création de vue de texte et convertit la vue à partir d’un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>— ce qui permet l’ajout de la commande à la chaîne de commande de l’interpréteur de commandes de Visual Studio — à un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Étant donné que cette classe est une exportation MEF, vous pouvez également l’utiliser pour importer les services qui sont requis par le Gestionnaire de commandes lui-même.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Pour implémenter le fournisseur de gestionnaire de commandes de saisie semi-automatique

1. Ajoutez un fichier nommé `TestCompletionCommandHandler`.

2. Ajoutez les instructions using :

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. Ajoutez une classe nommée `TestCompletionHandlerProvider` qui implémente <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Exporter cette classe avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> du « Gestionnaire d’achèvement jeton », un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « texte en clair » et un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. Importer le <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, qui permet la conversion d’un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> à un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, un <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>et un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> qui permet d’accéder aux services Visual Studio standard.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. Implémentez la <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> méthode pour instancier le Gestionnaire de commandes.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Implémenter le Gestionnaire de commandes de saisie semi-automatique
 Étant donné que la saisie semi-automatique des instructions sont déclenchée par des séquences de touches, vous devez implémenter le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface pour recevoir et traiter les séquences de touches qui déclenchent, valident et fermer la session de saisie semi-automatique.

#### <a name="to-implement-the-completion-command-handler"></a>Pour implémenter le Gestionnaire de commandes de saisie semi-automatique

1. Ajoutez une classe nommée `TestCompletionCommandHandler` qui implémente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Ajouter des champs privés pour le Gestionnaire de commandes suivant (à laquelle vous passez la commande), l’affichage de texte, le fournisseur du Gestionnaire de commandes (ce qui permet d’accéder à divers services) et une session de saisie semi-automatique :

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Ajoutez un constructeur qui définit l’affichage de texte et les champs du fournisseur et ajoute la commande à la chaîne de commande :

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Implémentez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode en passant la commande le long :

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Implémentez la méthode <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Lorsque cette méthode reçoit une séquence de touches, il effectuez l’une des opérations suivantes :

   - Autoriser le caractère à écrire dans la mémoire tampon et ensuite déclencher ou filtrer la saisie semi-automatique. (Les caractères imprimables faire.)

   - Valider la saisie semi-automatique, mais n’autorisent pas le caractère à écrire dans la mémoire tampon. (Espace blanc, **onglet**, et **entrée** cela lorsqu’une session de saisie semi-automatique est affichée.)

   - Autoriser la commande pour être transmis au gestionnaire suivant. (Toutes les autres commandes.)

     Étant donné que cette méthode peut afficher l’interface utilisateur, appelez <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> pour vous assurer qu’elle n’est pas appelée dans un contexte d’automation :

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Ce code est une méthode privée qui déclenche la session de saisie semi-automatique :

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. L’exemple suivant est une méthode privée qui annule son abonnement à la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> événement :

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Générer et tester le code
 Pour tester ce code, générez la solution CompletionTest et exécutez-le dans l’instance expérimentale.

#### <a name="to-build-and-test-the-completiontest-solution"></a>Pour générer et tester la solution CompletionTest

1. Générez la solution.

2. Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est démarrée.

3. Créez un fichier texte et tapez du texte qui inclut le mot « ajouter ».

4. Lorsque vous tapez tout d’abord « a » et ensuite « d », une liste qui contient « addition » et « adaptation » doit apparaître. Notez que l’addition est sélectionnée. Lorsque vous tapez un autre « d », la liste doit contenir « addition, uniquement » qui est maintenant sélectionnée. Vous pouvez valider « addition » en appuyant sur la **espace**, **onglet**, ou **entrée** de clé, ou ignorer la liste en tapant ÉCHAP ou une autre clé.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : Lier un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)