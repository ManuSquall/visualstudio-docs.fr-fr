---
title: "Proc&#233;dure pas &#224; pas&#160;: Cr&#233;ation d’un glyphe de marge | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), new - glyphe de marge"
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# Proc&#233;dure pas &#224; pas&#160;: Cr&#233;ation d’un glyphe de marge
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez personnaliser l’apparence des marges d’éditeur à l’aide des extensions de l’éditeur personnalisé. Cette procédure pas à pas place un glyphe personnalisé sur la marge des indicateurs chaque fois que le mot « todo » s’affiche dans un commentaire de code.  
  
## Composants requis  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Création d’un projet MEF  
  
1.  Créez un projet VSIX c\#. \(Dans le **Nouveau projet** boîte de dialogue, sélectionnez **Visual C\# \/ extensibilité**, puis **projet VSIX**.\) Nommez la solution `TodoGlyphTest`.  
  
2.  Ajouter un élément de projet du classifieur d’éditeur. Pour plus d'informations, consultez [Création d'une Extension avec un éditeur de modèle d'élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
## Définition du glyphe  
 Définissez un glyphe en implémentant le <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> interface.  
  
#### Pour définir le glyphe  
  
1.  Ajoutez un fichier de classe et nommez\-le `TodoGlyphFactory`.  
  
2.  Ajoutez le code suivant à l’aide de déclarations.  
  
     [!code-cs[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  Ajoutez une classe nommée `TodoGlyphFactory` qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-cs[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  Ajoutez un champ privé qui définit les dimensions du glyphe.  
  
     [!code-cs[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  Implémentez `GenerateGlyph` en définissant l’élément d’interface utilisateur utilisateur glyphe.`TodoTag` est défini plus loin dans cette procédure pas à pas.  
  
     [!code-cs[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  Ajoutez une classe nommée `TodoGlyphFactoryProvider` qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Exporter cette classe avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de « TodoGlyph », un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> d’après VsTextMarker, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « code » et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.  
  
     [!code-cs[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  Implémentez la <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> méthode en instanciant le `TodoGlyphFactory`.  
  
     [!code-cs[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## Définir une balise de tâches et la balise  
 Définissez la relation entre l’élément d’interface utilisateur que vous avez définie dans les étapes précédentes et la marge des indicateurs par création d’un type de balise et une balise et son exportation en utilisant un fournisseur de balise.  
  
#### Pour définir une balise de tâches et la balise  
  
1.  Ajoutez un nouveau fichier de classe au projet et nommez\-la `TodoTagger`.  
  
2.  Ajoutez les importations ci\-après.  
  
     [!code-cs[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  Ajoutez une classe nommée `TodoTag`.  
  
     [!code-cs[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  Modifier la classe nommée `TodoTagger` qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de type `TodoTag`.  
  
     [!code-cs[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  À la `TodoTagger` \(classe\), ajouter des champs privés pour un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> et pour le texte à rechercher dans la classification s’étend.  
  
     [!code-cs[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  Ajoutez un constructeur qui définit le classifieur.  
  
     [!code-cs[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> méthode en recherchant la classification de tous les couvre dont les noms incluent le mot « commentaire » et dont le texte contient le texte de recherche. Chaque fois que le texte recherché est trouvé, revenir génèrent un nouveau <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> de type `TodoTag`.  
  
     [!code-cs[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  Déclarez un `TagsChanged` événement.  
  
     [!code-cs[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. Ajoutez une classe nommée `TodoTaggerProvider` qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, et exportez\-le avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « code » et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.  
  
     [!code-cs[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. Importer le <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-cs[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> méthode en instanciant le `TodoTagger`.  
  
     [!code-cs[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## Création et test du code  
 Pour tester ce code, générez la solution TodoGlyphTest et exécutez\-le dans l’instance expérimentale.  
  
#### Pour générer et tester la solution TodoGlyphTest  
  
1.  Générez la solution.  
  
2.  Exécutez le projet en appuyant sur F5. Une deuxième instance de Visual Studio est instanciée.  
  
3.  Assurez\-vous que la marge des indicateurs s’affiche. \(Sur le **outils** menu, cliquez sur **Options**. Sur le **éditeur de texte** assurez\-vous que **marge des indicateurs** est sélectionnée.\)  
  
4.  Ouvrez un fichier de code qui comporte des commentaires. Ajoutez le mot « todo » à une des sections de commentaire.  
  
5.  Un cercle bleu clair qui a un contour bleu foncé doit apparaître dans la marge des indicateurs à gauche de la fenêtre de code.