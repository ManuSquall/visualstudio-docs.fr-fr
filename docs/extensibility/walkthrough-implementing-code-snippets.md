---
title: 'Procédure pas à pas : Mise en œuvre de Snippets de code Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: ba1b6e0852c1ec1b306938b791eed78e79d211ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697099"
---
# <a name="walkthrough-implement-code-snippets"></a>Procédure pas à pas : Implémentez des extraits de code
Vous pouvez créer des extraits de code et les inclure dans une extension d’éditeur afin que les utilisateurs de l’extension puissent les ajouter à leur propre code.

 Un extrait de code est un fragment de code ou d’un autre texte qui peut être incorporé dans un fichier. Pour voir tous les extraits qui ont été enregistrés pour des langages de programmation particuliers, sur le menu **Tools,** cliquez sur **Code Snippet Manager**. Pour insérer un extrait dans un fichier, cliquez à droite là où vous voulez l’extrait, cliquez sur Insert Snippet, ou **Surround With**, localiser l’extrait que vous voulez, puis double-cliquez dessus. Appuyez **sur Tab** ou **Shift**+**Tab** pour modifier les parties pertinentes de l’extrait, puis appuyez **sur Enter** ou **Esc** pour l’accepter. Pour plus d’informations, voir [Extraits de code](../ide/code-snippets.md).

 Un extrait de code est contenu dans un fichier XML qui a l’extension du nom de fichier .snippetMD. Un extrait peut contenir des champs qui sont mis en évidence après l’extrait est inséré afin que l’utilisateur puisse les trouver et les modifier. Un fichier d’extrait fournit également des informations pour le **gestionnaire de code D’extrait** afin qu’il puisse afficher le nom d’extrait dans la catégorie correcte. Pour plus d’informations sur le schéma d’extrait, voir [La référence des schémas de snippets code](../ide/code-snippets-schema-reference.md).

 Ce pas-là enseigne comment accomplir ces tâches :

1. Créez et enregistrez des extraits de code pour une langue spécifique.

2. Ajoutez la commande **Insert Snippet** à un menu raccourci.

3. Mettre en œuvre l’expansion des extraits.

   Cette procédure pas à pas est basée sur [Pas à pas: Affichage déclaration achèvement](../extensibility/walkthrough-displaying-statement-completion.md).

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-and-register-code-snippets"></a>Créer et enregistrer des extraits de code
 En règle générale, les extraits de code sont associés à un service linguistique enregistré. Cependant, vous n’avez <xref:Microsoft.VisualStudio.Package.LanguageService> pas à implémenter un extrait de code pour enregistrer. Au lieu de cela, il suffit de spécifier un GUID <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> dans le fichier d’index extrait, puis utiliser le même GUID dans le que vous ajoutez à votre projet.

 Les étapes suivantes montrent comment créer des extraits de code et les associer à un GUID spécifique.

1. Créez la structure d’annuaire suivante :

    **%InstallDir%-TestSnippets-Snippets-1033\\**

    où *%InstallDir%* est le dossier d’installation Visual Studio. (Bien que ce chemin soit généralement utilisé pour installer des extraits de code, vous pouvez spécifier n’importe quel chemin.)

2. Dans le dossier '1033', créez un fichier *.xml* et **nommez-le TestSnippets.xml**. (Bien que ce nom soit généralement utilisé pour un fichier d’index extrait, vous pouvez spécifier n’importe quel nom tant qu’il a une extension de nom de fichier *.xml.)* Ajoutez le texte suivant, puis supprimez le GUID de placeholder et ajoutez le vôtre.

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

3. Créez un fichier dans le dossier d’extrait, nommez-le **test,**`.snippet`puis ajoutez le texte suivant :

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

   Les étapes suivantes montrent comment enregistrer les extraits de code.

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Pour enregistrer des extraits de code pour un GUID spécifique

1. Ouvrez le projet **CompletionTest.** Pour plus d’informations sur la façon de créer ce projet, voir Procédure pas à [pas: Afficher l’achèvement de l’énoncé](../extensibility/walkthrough-displaying-statement-completion.md).

2. Dans le projet, ajoutez des références aux assemblées suivantes :

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.TextManager.Interop.8.0

    - microsoft.msxml (en anglais)

3. Dans le projet, ouvrez le fichier **source.extension.vsixmanifest.**

4. Assurez-vous que l’onglet **Actifs** contient un type de contenu **VsPackage** et que **le projet** est réglé au nom du projet.

5. Sélectionnez le projet CompletionTest et dans l’ensemble de fenêtre Propriétés **Générer Pkgdef Fichier** à **vrai**. Enregistrez le projet.

6. Ajoutez une `SnippetUtilities` classe statique au projet.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. Dans la classe SnippetUtilities, définissez un GUID et donnez-lui la valeur que vous avez utilisée dans le fichier *SnippetsIndex.xml.*

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. Ajoutez <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> le `TestCompletionHandler` à la classe. Cet attribut peut être ajouté à n’importe quelle classe publique ou interne (non statique) dans le projet. (Vous devrez peut-être ajouter une `using` directive pour le namespace Microsoft.VisualStudio.Shell.)

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Générez et exécutez le projet. Dans le cas expérimental de Visual Studio qui commence lorsque le projet est exécuté, l’extrait que vous venez d’enregistrer doit être affiché dans le **Code Snippets Manager** sous la langue **TestSnippets.**

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Ajouter la commande Insert Snippet au menu raccourci
 La commande **Insert Snippet** n’est pas incluse dans le menu raccourci pour un fichier texte. Par conséquent, vous devez activer la commande.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Pour ajouter la commande Insert Snippet au menu raccourci

1. Ouvrez `TestCompletionCommandHandler` le fichier de classe.

     Parce que cette <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>classe implémente , vous pouvez <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> activer la commande **Insert Snippet** dans la méthode. Avant d’activer la commande, vérifiez que cette méthode n’est pas appelée à l’intérieur d’une fonction d’automatisation parce que lorsque la commande **Insert Snippet** est cliqué, elle affiche l’interface utilisateur de cueilleur extrait (interface utilisateur).

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. Générez et exécutez le projet. Dans le cas expérimental, ouvrez un fichier qui a l’extension de nom de fichier *.zzz* et puis à droite-cliquez n’importe où en elle. La commande **Insert Snippet** doit apparaître sur le menu raccourci.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Mettre en œuvre l’expansion des extraits dans l’interface utilisateur de Snippet Picker
 Cette section montre comment implémenter l’extension de l’extrait de code afin que l’interface utilisateur de cueilleur d’extraits soit affichée lorsque **Insert Snippet** est cliqué sur le menu de raccourci. Un extrait de code est également élargi quand un utilisateur tape le raccourci code-extrait, puis appuie **sur Tab**.

 Pour afficher l’interface utilisateur de cueilleur d’extraits et pour permettre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> l’acceptation de l’approbation de la navigation et de l’extrait post-insertion, utilisez la méthode. L’insertion elle-même <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> est gérée par la méthode.

 La mise en œuvre de <xref:Microsoft.VisualStudio.TextManager.Interop> l’extension de l’extrait de code utilise des interfaces héritées. Lorsque vous traduisez des classes d’éditeur actuelles au code hérité, n’oubliez pas que les interfaces héritées utilisent une combinaison de numéros de ligne et de numéros de colonne pour spécifier les emplacements dans un tampon de texte, mais les classes actuelles utilisent un index. Par conséquent, si un tampon a trois lignes chacune de qui a 10 caractères (plus une nouvelle ligne, qui compte comme un personnage), le quatrième personnage sur la troisième ligne est à la position 27 dans la mise en œuvre actuelle, mais il est à la ligne 2, position 3 dans l’ancienne implémentation.

#### <a name="to-implement-snippet-expansion"></a>Mettre en œuvre l’expansion des extraits

1. Au fichier qui `TestCompletionCommandHandler` contient la classe, ajoutez les directives suivantes. `using`

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. Faites `TestCompletionCommandHandler` implémenter l’interface par la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> classe.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. Dans `TestCompletionCommandHandlerProvider` la classe, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>importer le .

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. Ajouter quelques champs privés pour les <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>interfaces d’extension de code et le .

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. Dans le constructeur `TestCompletionCommandHandler` de la classe, définir les champs suivants.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. Pour afficher le cueilleur d’extraits lorsque l’utilisateur clique sur la commande <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> **Insert Snippet,** ajoutez le code suivant à la méthode. (Pour rendre cette explication plus `Exec()`lisible, le code utilisé pour l’achèvement des relevés n’est pas indiqué; au lieu de cela, des blocs de code sont ajoutés à la méthode existante.) Ajoutez le bloc de code suivant après le code qui vérifie pour un personnage.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. Si un extrait a des champs qui peuvent être navigués, la session d’expansion est maintenue ouverte jusqu’à ce que l’expansion soit explicitement acceptée; si l’extrait n’a pas de champs, la `null` session <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> est fermée et est retournée comme par la méthode. Dans <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> la méthode, après l’extrait de l’interface utilisateur que vous avez ajouté dans l’étape précédente, ajoutez le code suivant pour gérer la navigation extraite (lorsque l’utilisateur appuie **Tab** ou **Shift**+**Tab** après l’insertion d’extrait).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. Pour insérer l’extrait de code lorsque l’utilisateur tape le raccourci <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> correspondant, puis appuie sur **Tab**, ajoutez du code à la méthode. La méthode privée qui insère l’extrait sera montrée dans une étape ultérieure. Ajoutez le code suivant après le code de navigation que vous avez ajouté dans l’étape précédente.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. Implémenter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> les méthodes de l’interface. Dans cette mise en œuvre, les seules méthodes d’intérêt sont <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Les autres méthodes <xref:Microsoft.VisualStudio.VSConstants.S_OK>devraient juste revenir .

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. Implémentez la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. La méthode d’aide qui insère réellement les extensions est couverte dans une étape ultérieure. Les <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> informations de ligne et de colonne <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>de fournit, que vous pouvez obtenir de la .

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. La méthode privée suivante insère un extrait de code, basé soit sur le raccourci, soit sur le titre et le chemin. Il appelle <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> alors la méthode avec l’extrait.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>Construire et tester l’expansion de l’extrait de code
 Vous pouvez tester si l’extension des extraits fonctionne dans votre projet.

1. Générez la solution. Lorsque vous exécutez ce projet dans le débbugger, une deuxième instance de Visual Studio est lancée.

2. Ouvrez un fichier texte et tapez un texte.

3. Cliquez à droite quelque part dans le texte, puis cliquez sur **Insert Snippet**.

4. L’interface utilisateur de cueilleur d’extraits devrait apparaître avec un pop-up qui dit **Champs de remplacement d’essai**. Double-cliquez sur le pop-up.

     L’extrait suivant doit être inséré.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     N’appuyez pas **sur Enter** ou **Esc**.

5. Appuyez **sur Tab** et **Shift**+**Tab** pour basculer entre "premier" et "deuxième".

6. Acceptez l’insertion en appuyant soit **entrez** ou **Esc**.

7. Dans une autre partie du texte, tapez "test" puis appuyez sur **Tab**. Parce que "test" est le raccourci code-extrait, l’extrait doit être inséré à nouveau.

## <a name="next-steps"></a>Étapes suivantes
