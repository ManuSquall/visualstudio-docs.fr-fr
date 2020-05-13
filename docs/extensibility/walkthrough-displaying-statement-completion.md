---
title: 'Procédure pas à pas : Affichage de l’achèvement de l’énoncé (en anglais seulement) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 1d2f5499511c9dc0bbb6711d0da630315384f8e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697412"
---
# <a name="walkthrough-display-statement-completion"></a>Procédure pas à pas : afficher la saisie semi-automatique des instructions
Vous pouvez implémenter l’achèvement de l’instruction basée sur la langue en définissant les identifiants pour lesquels vous souhaitez fournir l’achèvement, puis en déclenchant une session d’achèvement. Vous pouvez définir l’achèvement de l’instruction dans le contexte d’un service linguistique, définir votre propre extension de nom de fichier et le type de contenu, puis afficher l’achèvement pour ce type. Ou, vous pouvez déclencher l’achèvement d’un type de contenu existant, par exemple, "texte clair". Cette procédure pas à pas montre comment déclencher l’achèvement des relevés pour le type de contenu « texte clair », qui est le type de contenu des fichiers texte. Le type de contenu " texte " est l’ancêtre de tous les autres types de contenu, y compris les fichiers code et XML.

 L’achèvement de l’énoncé est généralement déclenché par la saisie de certains caractères, par exemple en tapant le début d’un identifiant tel que « l’utilisation ». Il est généralement rejeté en appuyant sur la **barre d’espace**, **Onglet**, ou **Entrez la** clé pour valider une sélection. Vous pouvez implémenter les fonctionnalités IntelliSense qui se déclenchent lorsque <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> vous tapez un personnage en <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> utilisant un gestionnaire de commande pour les frappes (l’interface) et un fournisseur de gestionnaires qui implémente l’interface. Pour créer la source d’achèvement, qui est la liste <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> des identifiants qui <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> participent à l’achèvement, implémenter l’interface et un fournisseur de source d’achèvement (l’interface). Les fournisseurs sont des composants du Cadre d’exténuabilité gérée (MEF). Ils sont responsables de l’exportation des classes de source et de <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>contrôleur et d’importer des <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>services et des courtiers, par exemple, le , qui permet la navigation dans le tampon de texte, et le , qui déclenche la session d’achèvement.

 Cette procédure pas à pas montre comment implémenter l’achèvement de l’instruction pour un ensemble d’identifiants codés en dur. Dans les implémentations complètes, le service linguistique et la documentation linguistique sont responsables de la fourniture de ce contenu.

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Créer un projet MEF

#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF

1. Créez un projet VSIX CMD. (Dans le dialogue du **nouveau projet,** sélectionnez **Visual C / Extensibility**, puis **VSIX Project**.) Nommez `CompletionTest`la solution .

2. Ajoutez un modèle d’élément Classificateur d’éditeur au projet. Pour plus d’informations, voir [Créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

4. Ajoutez les références suivantes au projet et assurez-vous `false`que **CopyLocal** est configuré à :

     Microsoft.VisualStudio.Éditeur

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.15.0

     Microsoft.VisualStudio.Shell.Immutable.10.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-the-completion-source"></a>Mettre en œuvre la source d’achèvement
 La source d’achèvement est responsable de la collecte de l’ensemble des identificateurs et de l’ajout du contenu à la fenêtre d’achèvement lorsqu’un utilisateur tape un déclencheur d’achèvement, comme les premières lettres d’un identifiant. Dans cet exemple, les identificateurs et leurs <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> descriptions sont codés en dur dans la méthode. Dans la plupart des utilisations du monde réel, vous utiliseriez le parseur de votre langue pour obtenir les jetons pour remplir la liste d’achèvement.

### <a name="to-implement-the-completion-source"></a>Pour mettre en œuvre la source d’achèvement

1. Ajoutez un fichier de classe et nommez-le `TestCompletionSource`.

2. Ajouter ces importations :

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. Modifier la déclaration `TestCompletionSource` de classe <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>pour qu’elle implémente :

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Ajouter des champs privés pour le fournisseur source, le tampon de texte et une liste d’objets <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> (qui correspondent aux identifiants qui participeront à la session d’achèvement):

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Ajouter un constructeur qui définit le fournisseur source et tampon. La `TestCompletionSourceProvider` classe est définie dans les étapes ultérieures :

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> méthode en ajoutant un ensemble d’achèvement qui contient les achèvements que vous souhaitez fournir dans le contexte. Chaque ensemble d’achèvement <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> contient un ensemble d’achèvements et correspond à un onglet de la fenêtre d’achèvement. (Dans les projets Visual Basic, les onglets de fenêtre d’achèvement sont nommés **communs** et **tous**.) La `FindTokenSpanAtPosition` méthode est définie dans l’étape suivante.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. La méthode suivante est utilisée pour trouver le mot actuel de la position du curseur :

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. Mettre `Dispose()` en œuvre la méthode :

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Mettre en œuvre le fournisseur de source d’achèvement
 Le fournisseur source d’achèvement est la partie composante MEF qui instantanéise la source d’achèvement.

### <a name="to-implement-the-completion-source-provider"></a>Mettre en œuvre le fournisseur de source d’achèvement

1. Ajouter une `TestCompletionSourceProvider` classe nommée <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>qui implémente . Exporter cette classe <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> avec un "texte <xref:Microsoft.VisualStudio.Utilities.NameAttribute> clair" et un "achèvement de test".

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. Importer <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>un , qui trouve le mot actuel dans la source d’achèvement.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. Implémenter la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> méthode pour instantané de la source d’achèvement.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Mettre en œuvre le fournisseur de gestionnaire de commande d’achèvement
 Le fournisseur de gestionnaire de <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>commande d’achèvement est dérivé d’un , <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>qui écoute pour un événement de création de vue de <xref:Microsoft.VisualStudio.Text.Editor.ITextView>texte et convertit la vue d’un -qui permet l’ajout de la commande à la chaîne de commande de la coque Visual Studio - à un . Étant donné que cette classe est une exportation MEF, vous pouvez également l’utiliser pour importer les services qui sont requis par le gestionnaire de commande lui-même.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Mettre en œuvre le fournisseur de gestionnaire de commande d’achèvement

1. Ajouter un `TestCompletionCommandHandler`fichier nommé .

2. Ajoutez ces directives à l’aide de directives :

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. Ajouter une `TestCompletionHandlerProvider` classe nommée <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>qui implémente . Exporter cette classe <xref:Microsoft.VisualStudio.Utilities.NameAttribute> avec un de "gestionnaire d’achèvement symbolique", un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "plaintext", et un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. Importer <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>le , qui <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> permet <xref:Microsoft.VisualStudio.Text.Editor.ITextView>la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>conversion d’un , a , et un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> qui permet l’accès à des services standard Visual Studio.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. Implémenter la <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> méthode pour instantanéer le gestionnaire de commande.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Mettre en œuvre le gestionnaire de commande d’achèvement
 Étant donné que l’achèvement de l’instruction est déclenché par des frappes, vous devez implémenter l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pour recevoir et traiter les frappes qui déclenchent, commettent et rejettent la session d’achèvement.

#### <a name="to-implement-the-completion-command-handler"></a>Mettre en œuvre le gestionnaire de commande d’achèvement

1. Ajouter une `TestCompletionCommandHandler` classe nommée <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>qui met en œuvre :

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Ajoutez des champs privés pour le prochain gestionnaire de commande (auquel vous passez la commande), la vue de texte, le fournisseur de gestionnaire de commande (qui permet l’accès à divers services) et une session d’achèvement :

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Ajoutez un constructeur qui définit la vue de texte et les champs du fournisseur, et ajoute la commande à la chaîne de commande :

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Implémenter la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode en passant la commande le long:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Implémentez la méthode <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Lorsque cette méthode reçoit une frappe, elle doit faire une de ces choses:

   - Laissez le personnage être écrit au tampon, puis déclencher ou filtrer l’achèvement. (Les personnages d’impression font cela.)

   - Engagez l’achèvement, mais ne permettez pas que le personnage soit écrit au tampon. (Whitespace, **Tab**, et **Enter** le faire quand une session d’achèvement est affichée.)

   - Laissez la commande passer au gestionnaire suivant. (Toutes les autres commandes.)

     Étant donné que cette méthode <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> peut afficher l’interface utilisateur, appelez pour vous assurer qu’elle n’est pas appelée dans un contexte d’automatisation :

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Ce code est une méthode privée qui déclenche la session d’achèvement :

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. L’exemple suivant est une méthode privée qui <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> désabonner de l’événement :

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Construire et tester le code
 Pour tester ce code, créez la solution CompletionTest et exécutez-la dans le cas expérimental.

#### <a name="to-build-and-test-the-completiontest-solution"></a>Construire et tester la solution CompletionTest

1. Générez la solution.

2. Lorsque vous exécutez ce projet dans le débbugger, une deuxième instance de Visual Studio est lancée.

3. Créez un fichier texte et tapez un texte qui inclut le mot «ajouter».

4. Comme vous tapez d’abord "a" puis "d", une liste qui contient "addition" et "adaptation" devrait apparaître. Notez que l’ajout est sélectionné. Lorsque vous tapez un autre "d", la liste ne doit contenir que "addition", qui est maintenant sélectionnée. Vous pouvez valider "addition" en appuyant sur la **barre d’espace,** **onglet**, ou **entrez** la clé, ou rejeter la liste en tapant Esc ou toute autre clé.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : liez un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
