---
title: 'Procédure pas à pas : implémentation d’extraits de code | Microsoft Docs'
description: Vous pouvez créer des extraits de code et les inclure dans une extension d’éditeur. Découvrez comment créer/inscrire des extraits de code à l’aide de cette procédure pas à pas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: leslierichardson95
ms.author: lerich
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: d55a11f30ad8b4397dc27247410d31b0b79267b7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078433"
---
# <a name="walkthrough-implement-code-snippets"></a>Procédure pas à pas : implémenter des extraits de code
Vous pouvez créer des extraits de code et les inclure dans une extension d’éditeur afin que les utilisateurs de l’extension puissent les ajouter à leur propre code.

 Un extrait de code est un fragment de code ou tout autre texte qui peut être incorporé dans un fichier. Pour afficher tous les extraits de code qui ont été inscrits pour des langages de programmation particuliers, dans le menu **Outils** , cliquez sur **Gestionnaire des extraits de code**. Pour insérer un extrait de code dans un fichier, cliquez avec le bouton droit sur l’emplacement où vous souhaitez l’extrait, cliquez sur Insérer un extrait ou **entourer de**, localisez l’extrait de code souhaité, puis double-cliquez dessus. Appuyez sur **Tab** ou **MAJ** + **Tab** pour modifier les parties pertinentes de l’extrait de code, puis appuyez sur **entrée** ou sur **Échap** pour l’accepter. Pour plus d’informations, consultez [extraits de code](../ide/code-snippets.md).

 Un extrait de code est contenu dans un fichier XML dont l’extension de nom de fichier est. snippet *. Un extrait de code peut contenir des champs qui sont mis en surbrillance après l’insertion de l’extrait de code afin que l’utilisateur puisse les trouver et les modifier. Un fichier d’extrait de code fournit également des informations pour le **Gestionnaire des extraits de code** afin qu’il puisse afficher le nom de l’extrait de code dans la catégorie appropriée. Pour plus d’informations sur le schéma d’extrait de code, consultez [référence de schéma des extraits de code](../ide/code-snippets-schema-reference.md).

 Cette procédure pas à pas explique comment accomplir ces tâches :

1. Créer et inscrire des extraits de code pour un langage spécifique.

2. Ajoutez la commande **Insérer un extrait** à un menu contextuel.

3. Implémentez le développement d’extraits.

   Cette procédure pas à pas est basée sur [procédure pas à pas : afficher la saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md).

## <a name="prerequisites"></a>Prérequis
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-and-register-code-snippets"></a>Créer et inscrire des extraits de code
 En règle générale, les extraits de code sont associés à un service de langage enregistré. Toutefois, il n’est pas nécessaire d’implémenter un <xref:Microsoft.VisualStudio.Package.LanguageService> pour inscrire des extraits de code. Au lieu de cela, il vous suffit de spécifier un GUID dans le fichier d’index d’extrait de code, puis d’utiliser le même GUID dans le <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> que vous ajoutez à votre projet.

 Les étapes suivantes montrent comment créer des extraits de code et les associer à un GUID spécifique.

1. Créez la structure de répertoire suivante :

    **%InstallDir%\TestSnippets\Snippets\1033\\**

    où *% INSTALLDIR%* est le dossier d’installation de Visual Studio. (Même si ce chemin d’accès est généralement utilisé pour installer des extraits de code, vous pouvez spécifier n’importe quel chemin d’accès.)

2. Dans le dossier \ 1033 \, créez un fichier *. xml* et nommez-le **TestSnippets.xml**. (Même si ce nom est généralement utilisé pour un fichier d’index d’extrait de code, vous pouvez spécifier n’importe quel nom, à condition qu’il ait une extension de nom de fichier *. xml* .) Ajoutez le texte suivant, puis supprimez le GUID de l’espace réservé et ajoutez le vôtre.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <SnippetCollection>
       <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">
           <SnippetDir>
               <OnOff>On</OnOff>
               <Installed>true</Installed>
               <Locale>1033</Locale>
               <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>
               <LocalizedName>Snippets</LocalizedName>
           </SnippetDir>
       </Language>
   </SnippetCollection>
   ```

3. Créez un fichier dans le dossier snippet, nommez-le **test** `.snippet` , puis ajoutez le texte suivant :

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
       <CodeSnippet Format="1.0.0">
           <Header>
               <Title>Test replacement fields</Title>
               <Shortcut>test</Shortcut>
               <Description>Code snippet for testing replacement fields</Description>
               <Author>MSIT</Author>
               <SnippetTypes>
                   <SnippetType>Expansion</SnippetType>
               </SnippetTypes>
           </Header>
           <Snippet>
               <Declarations>
                   <Literal>
                     <ID>param1</ID>
                       <ToolTip>First field</ToolTip>
                       <Default>first</Default>
                   </Literal>
                   <Literal>
                       <ID>param2</ID>
                       <ToolTip>Second field</ToolTip>
                       <Default>second</Default>
                   </Literal>
               </Declarations>
               <References>
                  <Reference>
                      <Assembly>System.Windows.Forms.dll</Assembly>
                  </Reference>
               </References>
               <Code Language="TestSnippets">
                   <![CDATA[MessageBox.Show("$param1$");
        MessageBox.Show("$param2$");]]>
               </Code>
           </Snippet>
       </CodeSnippet>
   </CodeSnippets>
   ```

   Les étapes suivantes montrent comment inscrire les extraits de code.

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Pour inscrire des extraits de code pour un GUID spécifique

1. Ouvrez le projet **CompletionTest** . Pour plus d’informations sur la création de ce projet, consultez [procédure pas à pas : affichage de la saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md).

2. Dans le projet, ajoutez des références aux assemblys suivants :

    - Microsoft. VisualStudio. TextManager. Interop

    - Microsoft. VisualStudio. TextManager. Interop. 8.0

    - Microsoft. MSXML

3. Dans le projet, ouvrez le fichier **source. extension. vsixmanifest** .

4. Assurez-vous que l’onglet **ressources** contient un type de contenu **VSPackage** et que ce **projet** est défini sur le nom du projet.

5. Sélectionnez le projet CompletionTest, puis dans la Fenêtre Propriétés définissez **générer le fichier pkgdef** sur **true**. Enregistrez le projet.

6. Ajoutez une `SnippetUtilities` classe statique au projet.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. Dans la classe SnippetUtilities, définissez un GUID et attribuez-lui la valeur que vous avez utilisée dans le fichier *SnippetsIndex.xml* .

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. Ajoutez <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> à la `TestCompletionHandler` classe. Cet attribut peut être ajouté à n’importe quelle classe publique ou interne (non statique) dans le projet. (Vous devrez peut-être ajouter une `using` directive pour l’espace de noms Microsoft. VisualStudio. Shell.)

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Générez et exécutez le projet. Dans l’instance expérimentale de Visual Studio qui démarre lorsque le projet est exécuté, l’extrait de code que vous venez d’inscrire doit être affiché dans le **Gestionnaire des extraits de code** sous le langage **TestSnippets** .

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Ajouter la commande Insérer un extrait au menu contextuel
 La commande **Insérer un extrait** de code n’est pas incluse dans le menu contextuel d’un fichier texte. Par conséquent, vous devez activer la commande.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Pour ajouter la commande Insérer un extrait au menu contextuel

1. Ouvrez le fichier de classe `TestCompletionCommandHandler`.

     Étant donné que cette classe implémente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , vous pouvez activer la commande **Insérer un extrait** de code dans la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode. Avant d’activer la commande, vérifiez que cette méthode n’est pas appelée à l’intérieur d’une fonction d’automatisation car, lorsque vous cliquez sur la commande **Insérer un extrait** , elle affiche l’interface utilisateur du sélecteur d’extraits de code.

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. Générez et exécutez le projet. Dans l’instance expérimentale, ouvrez un fichier ayant l’extension de nom de fichier *. zzz* , puis cliquez avec le bouton droit n’importe où dans celui-ci. La commande **Insérer un extrait** de code doit apparaître dans le menu contextuel.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Implémenter l’extension d’extrait dans l’interface utilisateur du sélecteur d’extraits
 Cette section montre comment implémenter l’expansion des extraits de code pour que l’interface utilisateur du sélecteur d’extraits de code s’affiche lorsque vous cliquez sur **Insérer un extrait** dans le menu contextuel. Un extrait de code est également développé quand un utilisateur tape le raccourci d’extrait de code, puis appuie sur la touche **Tab**.

 Pour afficher l’interface utilisateur du sélecteur d’extraits de code et activer la navigation et l’acceptation des extraits de code postérieurs à l’insertion, utilisez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode. L’insertion elle-même est gérée par la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> méthode.

 L’implémentation de l’expansion des extraits de code utilise des interfaces héritées <xref:Microsoft.VisualStudio.TextManager.Interop> . Quand vous traduisez des classes de l’éditeur en cours au code hérité, n’oubliez pas que les interfaces héritées utilisent une combinaison de numéros de ligne et de colonnes pour spécifier des emplacements dans une mémoire tampon de texte, mais les classes actuelles utilisent un index. Par conséquent, si une mémoire tampon comporte trois lignes qui ont chacune 10 caractères (plus un saut de ligne, qui compte comme un seul caractère), le quatrième caractère sur la troisième ligne se trouve à la position 27 dans l’implémentation actuelle, mais il se trouve à la ligne 2, position 3 dans l’ancienne implémentation.

#### <a name="to-implement-snippet-expansion"></a>Pour implémenter l’extension d’extrait

1. Ajoutez les directives suivantes au fichier qui contient la `TestCompletionCommandHandler` classe `using` .

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. Faites en sorte que la `TestCompletionCommandHandler` classe implémente l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interface.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. Dans la `TestCompletionCommandHandlerProvider` classe, importez le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> .

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. Ajoutez des champs privés pour les interfaces d’expansion de code et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. Dans le constructeur de la `TestCompletionCommandHandler` classe, définissez les champs suivants.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. Pour afficher le sélecteur d’extraits de code lorsque l’utilisateur clique sur la commande **Insérer un extrait** , ajoutez le code suivant à la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode. (Pour rendre cette explication plus lisible, le `Exec()` code utilisé pour la saisie semi-automatique des instructions n’est pas affiché ; à la place, les blocs de code sont ajoutés à la méthode existante.) Ajoutez le bloc de code suivant après le code qui recherche un caractère.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. Si un extrait de code contient des champs qui peuvent être parcourus, la session d’expansion est maintenue ouverte jusqu’à ce que l’expansion soit explicitement acceptée ; Si l’extrait de code n’a pas de champs, la session est fermée et est retournée comme `null` par la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> méthode. Dans la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode, après le code d’interface utilisateur du sélecteur d’extraits de code que vous avez ajouté à l’étape précédente, ajoutez le code suivant pour gérer la navigation dans les extraits de code (lorsque l’utilisateur appuie sur la touche **Tab** ou **MAJ** + **Tab** après l’insertion de l’extrait de code).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. Pour insérer l’extrait de code lorsque l’utilisateur tape le raccourci correspondant, puis appuie sur la **touche Tab**, ajoutez du code à la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode. La méthode privée qui insère l’extrait de code sera affichée dans une étape ultérieure. Ajoutez le code suivant après le code de navigation que vous avez ajouté à l’étape précédente.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. Implémentez les méthodes de l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interface. Dans cette implémentation, les seules méthodes intéressantes sont <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> . Les autres méthodes doivent simplement retourner <xref:Microsoft.VisualStudio.VSConstants.S_OK> .

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. Implémentez la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. La méthode d’assistance qui insère réellement les expansions est traitée dans une étape ultérieure. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>Fournit des informations sur les lignes et les colonnes, que vous pouvez extraire à partir de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. La méthode privée suivante insère un extrait de code, basé sur le raccourci ou sur le titre et le chemin d’accès. Il appelle ensuite la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> méthode avec l’extrait de code.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>Développement d’extraits de code de génération et de test
 Vous pouvez vérifier si l’extension d’extrait de code fonctionne dans votre projet.

1. Générez la solution. Quand vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est démarrée.

2. Ouvrez un fichier texte et tapez du texte.

3. Cliquez avec le bouton droit n’importe où dans le texte, puis cliquez sur **Insérer un extrait**.

4. L’interface utilisateur du sélecteur d’extraits de code doit apparaître avec une fenêtre contextuelle indiquant les **champs de remplacement des tests**. Double-cliquez sur la fenêtre contextuelle.

     L’extrait de code suivant doit être inséré.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     N’appuyez pas sur **entrée** ou sur **Échap**.

5. Appuyez sur les **touches** **Tab** et MAJ +  pour basculer entre « First » et « second ».

6. Acceptez l’insertion en appuyant sur **entrée** ou **Échap**.

7. Dans une autre partie du texte, tapez « test », puis appuyez sur la touche **Tab**. Étant donné que « test » est le raccourci d’extrait de code, l’extrait de code doit être inséré à nouveau.

## <a name="next-steps"></a>Étapes suivantes
