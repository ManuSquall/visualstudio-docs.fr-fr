---
title: 'Procédure pas à pas : Implémentation d’extraits de Code | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6fe91fd4e80c14e9b4cf59136fa6d3e0e003f554
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752063"
---
# <a name="walkthrough-implementing-code-snippets"></a>Procédure pas à pas : implémentation d’extraits de code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez créer des extraits de code et incluez-les dans une extension de l’éditeur, afin que les utilisateurs de l’extension de les ajouter à leur propre code.  
  
 Un extrait de code est un fragment de code ou autre texte qui peut être incorporé dans un fichier. Pour afficher tous les extraits de code qui ont été inscrits pour les langages de programmation particuliers, sur le **outils** menu, cliquez sur **Gestionnaire des extraits de Code**. Pour insérer un extrait de code dans un fichier, avec le bouton droit où vous souhaitez que l’extrait de code, cliquez sur **insérer un extrait** ou **entourer**, recherchez l’extrait de code, puis double-cliquez dessus. Appuyez sur TAB ou MAJ + TAB pour modifier les parties pertinentes de l’extrait de code, puis appuyez sur entrée ou ÉCHAP pour l’accepter. Pour plus d’informations, consultez [Extraits de code](../ide/code-snippets.md).  
  
 Un extrait de code est contenu dans un fichier XML qui a l’extension de nom de fichier .snippet. Un extrait de code peut contenir des champs qui sont mis en surbrillance après avoir inséré l’extrait de code afin que l’utilisateur peut rechercher et les modifier. Un fichier d’extrait de code fournit également des informations pour le **Gestionnaire des extraits de Code** pour qu’il puisse afficher le nom de l’extrait de code dans la catégorie appropriée. Pour plus d’informations sur le schéma d’extrait de code, consultez [référence de schéma des extraits de Code](../ide/code-snippets-schema-reference.md).  
  
 Cette procédure pas à pas explique comment accomplir ces tâches :  
  
1. Créez et inscrivez les extraits de code pour une langue spécifique.  
  
2. Ajouter le **insérer un extrait** commande à un menu contextuel.  
  
3. Implémenter l’expansion d’extrait de code.  
  
   Cette procédure pas à pas est basée sur [procédure pas à pas : affichage de saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-and-registering-code-snippets"></a>Création et enregistrement d’extraits de Code  
 En règle générale, les extraits de code sont associés à un service de langage enregistrés. Toutefois, vous n’avez pas à implémenter un <xref:Microsoft.VisualStudio.Package.LanguageService> pour inscrire des extraits de code. Au lieu de cela, spécifiez simplement un GUID dans le fichier d’index extrait et ensuite utiliser le même GUID dans le <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> que vous ajoutez à votre projet.  
  
 Les étapes suivantes montrent comment créer des extraits de code et les associer à un GUID spécifique.  
  
1. Créez la structure de répertoire suivante :  
  
    **%INSTALLDIR%\TestSnippets\Snippets\1033\\**  
  
    où *% INSTALLDIR%* est le dossier d’installation de Visual Studio. (Bien que ce chemin d’accès est généralement utilisé pour installer des extraits de code, vous pouvez spécifier n’importe quel chemin d’accès.)  
  
2. Dans le dossier \1033\, créez un fichier .xml et nommez-le **TestSnippets.xml**. (Bien que ce nom est généralement utilisé pour un fichier d’index extrait de code, vous pouvez spécifier n’importe quel nom tant qu’il a une extension de nom de fichier .xml.) Ajoutez le texte suivant, puis supprimer l’espace réservé GUID et d’ajouter vos propres.  
  
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
  
3. Créez un fichier dans le dossier d’extrait de code, nommez-le **tester**`.snippet`, puis ajoutez le texte suivant :  
  
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
  
#### <a name="to-register-code-snippets-for-a-specific-guid"></a>Pour inscrire des extraits de code pour un GUID spécifique  
  
1.  Ouvrez le **CompletionTest** projet. Pour plus d’informations sur la création de ce projet, consultez [procédure pas à pas : affichage de saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2.  Dans le projet, ajoutez des références aux assemblys suivants :  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   Microsoft.MSXML  
  
3.  Dans le projet, ouvrez le fichier source.extension.vsixmanifest.  
  
4.  Assurez-vous que le **actifs** onglet contient un **VsPackage** contenu type et qui **projet** est définie sur le nom du projet.  
  
5.  Sélectionnez le projet CompletionTest et dans la fenêtre Propriétés, définissez **générer le fichier Pkgdef** à **true**. Enregistrez le projet.  
  
6.  Ajouter un mappage statique `SnippetUtilities` classe au projet.  
  
     [!code-csharp[VSSDKCompletionTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#22)]
     [!code-vb[VSSDKCompletionTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#22)]  
  
7.  Dans la classe SnippetUtilities, définir un GUID et attribuez-lui la valeur que vous avez utilisé dans le fichier SnippetsIndex.xml.  
  
     [!code-csharp[VSSDKCompletionTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#23)]
     [!code-vb[VSSDKCompletionTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#23)]  
  
8.  Ajouter le <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> à la `TestCompletionHandler` classe. Cet attribut peut être ajouté à n’importe quelle classe (non statique) public ou interne dans le projet. (Vous devrez peut-être ajouter un `using` instruction pour l’espace de noms Microsoft.VisualStudio.Shell.)  
  
     [!code-csharp[VSSDKCompletionTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#24)]
     [!code-vb[VSSDKCompletionTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#24)]  
  
9. Générez et exécutez le projet. Dans l’instance expérimentale de Visual Studio qui démarre lorsque le projet est exécuté, l’extrait de code que vous venez d’inscrire doit être affiché dans le **Gestionnaire des extraits de Code** sous le **TestSnippets** langage.  
  
## <a name="adding-the-insert-snippet-command-to-the-shortcut-menu"></a>Ajout de la commande extrait de code d’insertion pour le Menu contextuel  
 Le **insérer un extrait** commande n’est pas incluse dans le menu contextuel pour un fichier texte. Par conséquent, vous devez activer la commande.  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Pour ajouter la commande Insérer un extrait au menu contextuel  
  
1.  Ouvrez le `TestCompletionCommandHandler` fichier de classe.  
  
     Étant donné que cette classe implémente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, vous pouvez activer le **insérer un extrait** commande dans le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> (méthode). Avant d’activer la commande, vérifiez que cette méthode n'est pas appelée à l’intérieur d’une fonction d’automatisation, car lorsque la **insérer un extrait** commande est activée, il affiche l’interface utilisateur du sélecteur extrait de code (IU).  
  
     [!code-csharp[VSSDKCompletionTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#25)]
     [!code-vb[VSSDKCompletionTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#25)]  
  
2.  Générez et exécutez le projet. Dans l’instance expérimentale, ouvrez un fichier portant l’extension de nom de fichier .zzz et ensuite avec le bouton droit n’importe où dans celui-ci. Le **insérer un extrait** commande doit apparaître dans le menu contextuel.  
  
## <a name="implementing-snippet-expansion-in-the-snippet-picker-ui"></a>Implémentation d’Expansion d’extrait de code dans le sélecteur d’extraits de l’interface utilisateur  
 Cette section montre comment implémenter l’expansion d’extrait de code afin que le sélecteur d’extraits de l’interface utilisateur est affiché lorsque **insérer un extrait** un clic sur le menu contextuel. Un extrait de code est également développé lorsqu’un utilisateur tape le raccourci d’extrait de code, puis appuie sur TAB.  
  
 Pour afficher le sélecteur d’extraits de l’interface utilisateur et pour activer la navigation et l’acceptation de l’extrait de code après insertion, utilisez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> (méthode). L’insertion proprement dite est gérée par le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> (méthode).  
  
 L’implémentation de l’expansion d’extrait de code utilise hérité <xref:Microsoft.VisualStudio.TextManager.Interop> interfaces. Lorsque vous traduisez des classes de l’éditeur actuel pour le code hérité, n’oubliez pas que les interfaces héritées utilisent une combinaison de numéros de ligne et de colonne pour spécifier les emplacements dans une mémoire tampon de texte, mais les classes actuels utilisent un seul index. Par conséquent, si une mémoire tampon a trois lignes chacun d’eux a dix caractères (plus un saut de ligne est comptabilisé comme un caractère de 1), le quatrième caractère sur la troisième ligne est à la position 27 dans l’implémentation actuelle, mais il est à la ligne 2, vous pouvez positionner 3 dans l’ancienne implémentation.  
  
#### <a name="to-implement-snippet-expansion"></a>Pour implémenter l’expansion d’extrait de code  
  
1.  Dans le fichier qui contient le `TestCompletionCommandHandler` de classe, ajoutez le code suivant `using` instructions.  
  
     [!code-csharp[VSSDKCompletionTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#26)]
     [!code-vb[VSSDKCompletionTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#26)]  
  
2.  Rendre le `TestCompletionCommandHandler` implémentent la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interface.  
  
     [!code-csharp[VSSDKCompletionTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#27)]
     [!code-vb[VSSDKCompletionTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#27)]  
  
3.  Dans le `TestCompletionCommandHandlerProvider` classe, importez le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.  
  
     [!code-csharp[VSSDKCompletionTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#28)]
     [!code-vb[VSSDKCompletionTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#28)]  
  
4.  Ajouter des champs privés pour les interfaces d’extension de code et le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#29)]
     [!code-vb[VSSDKCompletionTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#29)]  
  
5.  Dans le constructeur de la `TestCompletionCommandHandler` de classe, définissez les champs suivants.  
  
     [!code-csharp[VSSDKCompletionTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#30)]
     [!code-vb[VSSDKCompletionTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#30)]  
  
6.  Pour afficher le sélecteur d’extrait de code lorsque l’utilisateur clique sur le **insérer un extrait** de commande, ajoutez le code suivant à la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> (méthode). (Pour améliorer la lisibilité de cette explication, le code de Exec() qui est utilisé pour compléter l’instruction n’est pas indiqué ; au lieu de cela, les blocs de code sont ajoutés à la méthode existante). Ajoutez le bloc de code suivant après le code qui vérifie un caractère.  
  
     [!code-csharp[VSSDKCompletionTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#31)]
     [!code-vb[VSSDKCompletionTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#31)]  
  
7.  Si un extrait de code comporte des champs qui peuvent être parcourues, la session d’expansion est maintenue ouverte jusqu'à ce que l’expansion est acceptée explicitement ; Si l’extrait de code ne comporte aucun champ, la session est fermée et qu’elle est retournée en tant que `null` par le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> (méthode). Dans le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> (méthode), après le sélecteur d’extraits de code d’interface utilisateur que vous avez ajouté à l’étape précédente, ajoutez le code suivant pour gérer la navigation de l’extrait de code (lorsque l’utilisateur appuie sur TAB ou MAJ + TAB après l’insertion d’extraits).  
  
     [!code-csharp[VSSDKCompletionTest#32](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#32)]
     [!code-vb[VSSDKCompletionTest#32](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#32)]  
  
8.  Pour insérer l’extrait de code lorsque l’utilisateur tape le raccourci correspondant, puis appuie sur TAB, ajoutez le code à la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> (méthode). La méthode privée qui insère l’extrait de code s’affichera dans une étape ultérieure. Ajoutez le code suivant après le code de navigation que vous avez ajouté à l’étape précédente.  
  
     [!code-csharp[VSSDKCompletionTest#33](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#33)]
     [!code-vb[VSSDKCompletionTest#33](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#33)]  
  
9. Implémenter les méthodes de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interface. Dans cette implémentation, les seules méthodes dignes d’intérêt sont <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Les autres méthodes doivent simplement retourner <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
     [!code-csharp[VSSDKCompletionTest#34](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#34)]
     [!code-vb[VSSDKCompletionTest#34](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#34)]  
  
10. Implémentez la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. La méthode d’assistance qui insère en fait les expansions point sera abordée dans une étape ultérieure. Le <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> fournit des informations de ligne et colonne, que vous pouvez obtenir à partir de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#35](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#35)]
     [!code-vb[VSSDKCompletionTest#35](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#35)]  
  
11. La méthode privée suivante insère un extrait de code, basé sur le raccourci ou sur le titre et le chemin d’accès. Il appelle ensuite la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> méthode avec l’extrait de code.  
  
     [!code-csharp[VSSDKCompletionTest#36](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#36)]
     [!code-vb[VSSDKCompletionTest#36](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#36)]  
  
## <a name="building-and-testing-code-snippet-expansion"></a>Génération et test d’Expansion d’extrait de Code  
 Vous pouvez tester si l’expansion d’extrait de code fonctionne dans votre projet.  
  
1.  Générez la solution. Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
2.  Ouvrez un fichier texte et tapez du texte.  
  
3.  Avec le bouton droit quelque part dans le texte, puis cliquez sur **insérer un extrait**.  
  
4.  Le sélecteur d’extraits de l’interface utilisateur doit apparaître avec une fenêtre contextuelle qui dit **tester des champs de remplacement**. Double-cliquez sur la fenêtre contextuelle.  
  
     L’extrait de code suivant doit être inséré.  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     N’appuyez pas sur entrée ou ÉCHAP.  
  
5.  Appuyez sur TAB et MAJ + TAB pour basculer entre « first » et « seconde ».  
  
6.  Accepter l’insertion en appuyant sur entrée ou ÉCHAP.  
  
7.  Dans une autre partie du texte, tapez « test » et appuyez sur TAB. Étant donné que « test » est le raccourci d’extrait de code, l’extrait de code doit être inséré à nouveau.  
  
## <a name="next-steps"></a>Étapes suivantes

