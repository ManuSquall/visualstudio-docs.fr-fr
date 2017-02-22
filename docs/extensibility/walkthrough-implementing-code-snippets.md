---
title: "Proc&#233;dure pas &#224; pas : Impl&#233;mentation d&#39;extraits de Code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Proc&#233;dure pas &#224; pas : Impl&#233;mentation d&#39;extraits de Code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez créer des extraits de code et les inclure dans une extension de l'éditeur afin que les utilisateurs de l'extension de les ajouter à leur propre code.  
  
 Un extrait de code est un fragment de code ou de texte qui peut être incorporé dans un fichier. Pour afficher tous les extraits de code qui ont été enregistrés pour les langages de programmation spécifiques, sur le **outils** menu, cliquez sur **Gestionnaire des extraits de Code**. Pour insérer un extrait de code dans un fichier, avec le bouton droit où vous souhaitez que l'extrait, cliquez sur **Insérer un extrait de** ou **Entourer**, recherchez l'extrait de code, puis double\-cliquez dessus. Appuyez sur TAB ou MAJ \+ TAB pour modifier les parties pertinentes de l'extrait de code, puis appuyez sur entrée ou ÉCHAP pour accepter. Pour plus d'informations, consultez [Extraits de code](../ide/code-snippets.md).  
  
 Un extrait de code est contenu dans un fichier XML qui a l'extension de nom de fichier .snippet. Un extrait de code peut contenir des champs qui sont mis en surbrillance après avoir inséré l'extrait de code afin que l'utilisateur peut rechercher et les modifier. Un fichier d'extrait de code fournit également des informations pour le **Gestionnaire des extraits de Code** pour qu'il puisse afficher le nom de l'extrait de code dans la catégorie appropriée. Pour plus d'informations sur le schéma de l'extrait de code, consultez [Référence de schéma des extraits de code](../ide/code-snippets-schema-reference.md).  
  
 Cette procédure pas à pas explique comment effectuer ces tâches :  
  
1.  Créer et enregistrer des extraits de code pour une langue spécifique.  
  
2.  Ajouter le **Insérer un extrait de** commande à un menu contextuel.  
  
3.  Implémenter l'expansion de l'extrait de code.  
  
 Cette procédure pas à pas est basée sur [Procédure pas à pas : Affichage de saisie semi\-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## Composants requis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement Visual Studio. Pour plus d'informations, consultez [Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Création et enregistrement d'extraits de Code  
 En règle générale, les extraits de code sont associés à un service de langage enregistré. Toutefois, vous n'avez pas à implémenter un <xref:Microsoft.VisualStudio.Package.LanguageService> pour inscrire des extraits de code. Au lieu de cela, spécifiez simplement un GUID dans le fichier d'index extrait et ensuite utiliser le même GUID dans le <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> que vous ajoutez à votre projet.  
  
 Les étapes suivantes montrent comment créer des extraits de code et les associer à un GUID spécifique.  
  
1.  Créez la structure de répertoires suivante :  
  
     **%INSTALLDIR%\\TestSnippets\\Snippets\\1033\\**  
  
     où *% INSTALLDIR%* est le dossier d'installation de Visual Studio. \(Bien que ce chemin d'accès est généralement utilisé pour installer les extraits de code, vous pouvez spécifier un chemin d'accès.\)  
  
2.  Dans le dossier \\1033\\, créez un fichier .xml et nommez\-la **TestSnippets.xml**. \(Bien que ce nom est généralement utilisé pour un fichier d'index extrait de code, vous pouvez spécifier n'importe quel nom tant qu'il a une extension de nom de fichier .xml.\) Ajoutez le texte suivant, puis supprimer l'espace réservé GUID et ajouter les vôtres.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?> <SnippetCollection> <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}"> <SnippetDir> <OnOff>On</OnOff> <Installed>true</Installed> <Locale>1033</Locale> <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath> <LocalizedName>Snippets</LocalizedName> </SnippetDir> </Language> </SnippetCollection>  
    ```  
  
3.  Créez un fichier dans le dossier d'extrait de code, nommez\-le **test**`.snippet`, puis ajoutez le texte suivant :  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?> <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet"> <CodeSnippet Format="1.0.0"> <Header> <Title>Test replacement fields</Title> <Shortcut>test</Shortcut> <Description>Code snippet for testing replacement fields</Description> <Author>MSIT</Author> <SnippetTypes> <SnippetType>Expansion</SnippetType> </SnippetTypes> </Header> <Snippet> <Declarations> <Literal> <ID>param1</ID> <ToolTip>First field</ToolTip> <Default>first</Default> </Literal> <Literal> <ID>param2</ID> <ToolTip>Second field</ToolTip> <Default>second</Default> </Literal> </Declarations> <References> <Reference> <Assembly>System.Windows.Forms.dll</Assembly> </Reference> </References> <Code Language="TestSnippets"> <![CDATA[MessageBox.Show("$param1$"); MessageBox.Show("$param2$");]]> </Code> </Snippet> </CodeSnippet> </CodeSnippets>  
    ```  
  
 Les étapes suivantes montrent comment inscrire les extraits de code.  
  
#### Pour inscrire des extraits de code pour un GUID spécifique  
  
1.  Ouvrez la **CompletionTest** projet. Pour plus d'informations sur la création de ce projet, consultez [Procédure pas à pas : Affichage de saisie semi\-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2.  Dans le projet, ajoutez des références aux assemblys suivants :  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   Microsoft.MSXML  
  
3.  Dans le projet, ouvrez le fichier source.extension.vsixmanifest.  
  
4.  Assurez\-vous que le **actifs** onglet contient un **VsPackage** type, du contenu **projet** est défini sur le nom du projet.  
  
5.  Sélectionnez le projet CompletionTest et dans la fenêtre Propriétés, définissez **génération d'un fichier Pkgdef** à **true**. Enregistrez le projet.  
  
6.  Ajouter un mappage statique `SnippetUtilities` classe au projet.  
  
     [!code-cs[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  Dans la classe SnippetUtilities, définir un GUID et donnez\-lui la valeur que vous avez utilisé dans le fichier SnippetsIndex.xml.  
  
     [!code-cs[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  Ajouter la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> à la `TestCompletionHandler` classe. Cet attribut peut être ajouté à toute classe \(non statique\) public ou interne dans le projet. \(Vous devrez peut\-être ajouter un `using` instruction pour l'espace de noms Microsoft.VisualStudio.Shell.\)  
  
     [!code-cs[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. Générez et exécutez le projet. Dans l'instance expérimentale de Visual Studio qui démarre lorsque le projet est exécuté, l'extrait de code que vous venez d'inscrire doit être affiché dans le **Gestionnaire des extraits de Code** sous le **TestSnippets** language.  
  
## Ajout de la commande d'insertion extrait de code dans le Menu contextuel  
 Le **Insérer un extrait de** commande n'est pas incluse dans le menu contextuel pour un fichier texte. Par conséquent, vous devez activer la commande.  
  
#### Pour ajouter la commande Insérer un extrait dans le menu contextuel  
  
1.  Ouvrez la `TestCompletionCommandHandler` fichier de classe.  
  
     Étant donné que cette classe implémente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, vous pouvez activer la **Insérer un extrait de** dans le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> \(méthode\). Avant d'activer la commande, vérifiez que cette méthode n'est pas en cours appelée à l'intérieur d'une fonction d'automatisation, car lorsque le **Insérer un extrait de** commande est activée, il affiche l'interface utilisateur du sélecteur extrait \(UI\).  
  
     [!code-cs[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  Générez et exécutez le projet. Dans l'instance expérimentale, ouvrez un fichier ayant l'extension de nom de fichier .zzz et ensuite avec le bouton droit n'importe où dans celui\-ci. Le **Insérer un extrait de** commande doit apparaître dans le menu contextuel.  
  
## L'implémentation d'extension extrait dans le sélecteur d'extrait de l'interface utilisateur  
 Cette section montre comment implémenter l'expansion d'extrait de code afin que le sélecteur d'extrait de l'interface utilisateur est affiché lorsque **Insérer un extrait de** est sélectionné dans le menu contextuel. Un extrait de code est également étendu lorsqu'un utilisateur tape le raccourci d'extrait de code, puis appuie sur TAB.  
  
 Pour afficher le sélecteur d'extrait de l'interface utilisateur et pour activer la navigation et l'acceptation de l'extrait de code après d'insertion, utilisez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode. L'insertion proprement dite est gérée par le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> \(méthode\).  
  
 L'implémentation d'expansion d'extrait de code utilise hérité <xref:Microsoft.VisualStudio.TextManager.Interop> interfaces. Lorsque vous traduisez des classes d'éditeur actuel pour le code hérité, n'oubliez pas que les interfaces héritées utilisent une combinaison de numéros de ligne et de colonne pour spécifier les emplacements dans la mémoire tampon de texte, mais les classes actuelles utilisent un seul index. Par conséquent, si une mémoire tampon a trois lignes chacun d'eux comporte dix caractères \(plus un saut de ligne, qui comptent comme caractère de 1\), le quatrième caractère sur la troisième ligne est à la position 27 dans l'implémentation actuelle, mais il est à la ligne 2, placez la valeur 3 dans l'ancienne implémentation.  
  
#### Pour implémenter l'expansion de l'extrait de code  
  
1.  Dans le fichier qui contient le `TestCompletionCommandHandler` de classe, ajoutez le code suivant `using` instructions.  
  
     [!code-cs[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  Rendre la `TestCompletionCommandHandler` classe implémentent la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interface.  
  
     [!code-cs[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  Dans la `TestCompletionCommandHandlerProvider` classe, importez le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.  
  
     [!code-cs[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  Ajoutez des champs privés pour les interfaces d'extension de code et le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-cs[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  Dans le constructeur de la `TestCompletionCommandHandler` de classe, définissez les champs suivants.  
  
     [!code-cs[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  Pour afficher le sélecteur d'extrait de code lorsque l'utilisateur clique sur le **Insérer un extrait de** de commande, ajoutez le code suivant à la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> \(méthode\). \(Pour rendre cette explication plus lisible, le code de Exec\(\) qui est utilisé pour compléter l'instruction n'est pas indiqué ; au lieu de cela, les blocs de code sont ajoutés à la méthode existante\). Ajoutez le bloc de code suivant après le code qui vérifie un caractère.  
  
     [!code-cs[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  Si un extrait de code comporte des champs qui peuvent être parcourus, la session d'extension reste ouverte jusqu'à ce que l'expansion est explicitement acceptée ; Si l'extrait de code ne comporte aucun champ, la session est fermée et qu'elle est retournée en tant que `null` par le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> \(méthode\). Dans le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> \(méthode\), après le sélecteur d'extraits de code d'interface utilisateur que vous avez ajouté à l'étape précédente, ajoutez le code suivant pour gérer la navigation de l'extrait de code \(lorsque l'utilisateur appuie sur la touche TAB ou MAJ \+ TAB après l'insertion d'extrait de code\).  
  
     [!code-cs[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  Pour insérer l'extrait de code lorsque l'utilisateur tape le raccourci correspondant, puis appuie sur TAB, ajoutez le code à le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> \(méthode\). La méthode privée qui insère l'extrait de code s'affichera dans une étape ultérieure. Ajoutez le code suivant après le code de navigation que vous avez ajouté à l'étape précédente.  
  
     [!code-cs[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. Implémentez les méthodes de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interface. Dans cette implémentation, les seules méthodes dignes d'intérêt sont <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Les autres méthodes doivent simplement retourner <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
     [!code-cs[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. Implémentez la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. La méthode d'assistance qui insère en fait les expansions sera abordée dans une étape ultérieure. Le <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> fournit des informations de ligne et de colonne, que vous pouvez obtenir à partir de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-cs[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. La méthode privée suivante insère un extrait de code, basé sur le raccourci ou sur le titre et le chemin d'accès. Il appelle ensuite la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> méthode avec l'extrait de code.  
  
     [!code-cs[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## Génération et test d'extension extrait de Code  
 Vous pouvez tester si l'expansion de l'extrait de code fonctionne dans votre projet.  
  
1.  Générez la solution. Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
2.  Ouvrez un fichier texte et tapez du texte.  
  
3.  Avec le bouton droit quelque part dans le texte, puis cliquez sur **Insérer un extrait de**.  
  
4.  Le sélecteur d'extrait de l'interface utilisateur doit apparaître avec une fenêtre contextuelle qui dit **tester des champs de remplacement**. Double\-cliquez sur le menu contextuel.  
  
     L'extrait suivant doit être inséré.  
  
    ```  
    MessageBox.Show("first"); MessageBox.Show("second");  
    ```  
  
     N'appuyez pas sur entrée ou ÉCHAP.  
  
5.  Appuyez sur TAB et MAJ \+ TAB pour basculer entre la « première » et « seconde ».  
  
6.  Accepter l'insertion en appuyant sur entrée ou ÉCHAP.  
  
7.  Dans une autre partie du texte, tapez « test » et appuyez sur TAB. Étant donné que « test » est le raccourci d'extrait de code, l'extrait de code doit être inséré à nouveau.  
  
## Étapes suivantes