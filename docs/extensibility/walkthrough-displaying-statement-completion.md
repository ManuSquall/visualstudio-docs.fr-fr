---
title: 'Procédure pas à pas : affichage de la saisie semi-automatique des instructions Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: madskristensen
ms.author: madsk
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 82ce8a1b9cbc79925ff2f4a1c1df9d832bb96f7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632517"
---
# <a name="walkthrough-display-statement-completion"></a>Procédure pas à pas : saisie semi-automatique des instructions
Vous pouvez implémenter la saisie semi-automatique des instructions basées sur le langage en définissant les identificateurs pour lesquels vous souhaitez fournir la saisie semi-automatique, puis en déclenchant une session de saisie semi-automatique. Vous pouvez définir la saisie semi-automatique des instructions dans le contexte d’un service de langage, définir votre propre extension de nom de fichier et le type de contenu, puis afficher la saisie semi-automatique uniquement pour ce type. Ou vous pouvez déclencher l’achèvement d’un type de contenu existant, par exemple, « texte en clair ». Cette procédure pas à pas montre comment déclencher la saisie semi-automatique des instructions pour le type de contenu « texte en clair », qui est le type de contenu des fichiers texte. Le type de contenu « texte » est l’ancêtre de tous les autres types de contenu, y compris le code et les fichiers XML.

 La saisie semi-automatique des instructions est généralement déclenchée par la saisie de certains caractères, par exemple en tapant le début d’un identificateur, tel que « using ». En général, il est rejeté en appuyant sur la **barre d’espace**, sur la touche **Tab**ou sur la touche **entrée** pour valider une sélection. Vous pouvez implémenter les fonctionnalités IntelliSense qui se déclenchent lors de la saisie d’un caractère à l’aide d’un gestionnaire de commandes pour les séquences de touches (l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) et d’un fournisseur de gestionnaires qui implémente l’interface <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Pour créer la source de saisie semi-automatique, qui est la liste des identificateurs qui participent à la saisie semi-automatique, implémentez l’interface <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> et un fournisseur de source de saisie semi-automatique (l’interface <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>). Les fournisseurs sont des composants de Managed Extensibility Framework (MEF). Ils sont chargés d’exporter les classes source et de contrôleur et d’importer les services et les courtiers, par exemple, le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, qui permet la navigation dans la mémoire tampon de texte, et le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, qui déclenche la session de saisie semi-automatique.

 Cette procédure pas à pas montre comment implémenter la saisie semi-automatique des instructions pour un ensemble d’identificateurs codés en dur. Dans les implémentations complètes, le service de langage et la documentation du langage sont responsables de la fourniture de ce contenu.

## <a name="prerequisites"></a>Configuration requise
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Créer un projet MEF

#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF

1. Créez un C# projet VSIX. (Dans la boîte de dialogue **nouveau projet** , sélectionnez **Visual C# /extensibilité**, puis **projet VSIX**.) Nommez la solution `CompletionTest`.

2. Ajoutez un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

4. Ajoutez les références suivantes au projet et assurez-vous que **CopyLocal** a la valeur `false` :

     Microsoft. VisualStudio. Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft. VisualStudio. OLE. Interop

     Microsoft. VisualStudio. Shell. 14.0

     Microsoft. VisualStudio. Shell. immuable. 10.0

     Microsoft. VisualStudio. TextManager. Interop

## <a name="implement-the-completion-source"></a>Implémenter la source de saisie semi-automatique
 La source de saisie semi-automatique est responsable de la collecte de l’ensemble des identificateurs et de l’ajout du contenu à la fenêtre de saisie semi-automatique lorsqu’un utilisateur tape un déclencheur de saisie semi-automatique, par exemple les premières lettres d’un identificateur. Dans cet exemple, les identificateurs et leurs descriptions sont codés en dur dans la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A>. Dans la plupart des utilisations réelles, vous pouvez utiliser l’analyseur de votre langage pour récupérer les jetons afin de remplir la liste de saisie semi-automatique.

### <a name="to-implement-the-completion-source"></a>Pour implémenter la source de saisie semi-automatique

1. Ajoutez un fichier de classe et nommez-le `TestCompletionSource`.

2. Ajoutez ces importations :

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. Modifiez la déclaration de classe pour `TestCompletionSource` afin qu’elle implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> :

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Ajoutez des champs privés pour le fournisseur source, la mémoire tampon de texte et une liste d’objets <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> (qui correspondent aux identificateurs qui feront partie de la session de saisie semi-automatique) :

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Ajoutez un constructeur qui définit le fournisseur et la mémoire tampon source. La classe `TestCompletionSourceProvider` est définie dans les étapes ultérieures :

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> en ajoutant un jeu de saisies semi-automatiques qui contient les saisies semi-automatiques que vous souhaitez fournir dans le contexte. Chaque jeu de saisies semi-automatiques contient un ensemble de saisies semi-automatiques <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> et correspond à un onglet de la fenêtre de saisie semi-automatique. (Dans Visual Basic projets, les onglets de la fenêtre de saisie semi-automatique sont nommés **Common** et **All**.) La méthode `FindTokenSpanAtPosition` est définie à l’étape suivante.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. La méthode suivante est utilisée pour rechercher le mot actuel à partir de la position du curseur :

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. Implémentez la méthode `Dispose()` :

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Implémenter le fournisseur de la source de saisie semi-automatique
 Le fournisseur de la source de saisie semi-automatique est le composant MEF qui instancie la source de saisie semi-automatique.

### <a name="to-implement-the-completion-source-provider"></a>Pour implémenter le fournisseur de la source de saisie semi-automatique

1. Ajoutez une classe nommée `TestCompletionSourceProvider` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Exportez cette classe avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « texte en clair » et un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de « fin de test ».

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. Importez un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, qui recherche le mot actuel dans la source de saisie semi-automatique.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> pour instancier la source de saisie semi-automatique.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Implémenter le fournisseur du gestionnaire de commandes de saisie semi-automatique
 Le fournisseur du gestionnaire de commandes de saisie semi-automatique est dérivé d’un <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, qui écoute un événement de création d’une vue de texte et convertit la vue d’une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, ce qui permet l’ajout de la commande à la chaîne de commande du shell Visual Studio, à un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Étant donné que cette classe est une exportation MEF, vous pouvez également l’utiliser pour importer les services requis par le gestionnaire de commandes lui-même.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Pour implémenter le fournisseur du gestionnaire de commandes de saisie semi-automatique

1. Ajoutez un fichier nommé `TestCompletionCommandHandler`.

2. Ajoutez les directives using suivantes :

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. Ajoutez une classe nommée `TestCompletionHandlerProvider` qui implémente <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Exportez cette classe avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de « gestionnaire d’achèvement de jeton », un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « texte en clair » et un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. Importez le <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, qui permet la conversion d’un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> en <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, un <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> et un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> qui permet d’accéder aux services Visual Studio standard.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. Implémentez la méthode <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> pour instancier le gestionnaire de commandes.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Implémenter le gestionnaire de commandes d’achèvement
 Étant donné que la saisie semi-automatique des instructions est déclenchée par les séquences de touches, vous devez implémenter l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pour recevoir et traiter les séquences de touches qui déclenchent, valident et ignorent la session de saisie semi-automatique.

#### <a name="to-implement-the-completion-command-handler"></a>Pour implémenter le gestionnaire de commandes de saisie semi-automatique

1. Ajoutez une classe nommée `TestCompletionCommandHandler` qui implémente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Ajoutez des champs privés pour le gestionnaire de commandes suivant (vers lequel vous transmettez la commande), l’affichage de texte, le fournisseur du gestionnaire de commandes (qui permet d’accéder à divers services) et une session de saisie semi-automatique :

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Ajoutez un constructeur qui définit l’affichage de texte et les champs de fournisseur, puis ajoute la commande à la chaîne de commande :

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Implémentez la méthode <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> en passant la commande sur :

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Implémentez la méthode <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Quand cette méthode reçoit une séquence de touches, elle doit effectuer l’une des opérations suivantes :

   - Autorisez l’écriture du caractère dans la mémoire tampon, puis déclenchez ou filtrez la saisie semi-automatique. (Les caractères d’impression le font.)

   - Validez la saisie semi-automatique, mais n’autorisez pas l’écriture du caractère dans la mémoire tampon. (Espace, **tabulation**, puis **Entrez** cette opération lorsqu’une session de saisie semi-automatique est affichée.)

   - Autorise la transmission de la commande au gestionnaire suivant. (Toutes les autres commandes.)

     Étant donné que cette méthode peut afficher l’interface utilisateur, appelez <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> pour vous assurer qu’elle n’est pas appelée dans un contexte d’automatisation :

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Ce code est une méthode privée qui déclenche la session de saisie semi-automatique :

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. L’exemple suivant est une méthode privée qui annule l’abonnement de l’événement <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> :

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Générer et tester le code
 Pour tester ce code, générez la solution CompletionTest et exécutez-la dans l’instance expérimentale.

#### <a name="to-build-and-test-the-completiontest-solution"></a>Pour générer et tester la solution CompletionTest

1. Générez la solution.

2. Quand vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est démarrée.

3. Créez un fichier texte et tapez du texte qui contient le mot « ajouter ».

4. Lorsque vous tapez en premier « a », puis « d », une liste contenant « addition » et « adaptation » doit apparaître. Notez que l’addition est sélectionnée. Lorsque vous tapez un autre « d », la liste doit contenir uniquement « addition », qui est maintenant sélectionnée. Vous pouvez valider « addition » en appuyant sur la **barre d’espace**, l' **onglet**ou la touche **entrée** , ou faire disparaître la liste en tapant ESC ou toute autre touche.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : liaison d’un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
