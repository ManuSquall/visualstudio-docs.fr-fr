---
title: 'Procédure pas à pas : Création d’un glyphe de marge | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d22607dd4e32ac29a773b6217056c2484121cd9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952853"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>Procédure pas à pas : Création d'un glyphe de marge
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez personnaliser l’apparence des marges de l’éditeur à l’aide des extensions de l’éditeur personnalisé. Cette procédure pas à pas place un glyphe personnalisé sur la marge des indicateurs chaque fois que le mot « todo » s’affiche dans un commentaire de code.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Création d’un projet MEF  
  
1.  Créez un projet C# VSIX. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual C# / extensibilité**, puis **projet VSIX**.) Nommez la solution `TodoGlyphTest`.  
  
2.  Ajouter un élément de projet classifieur d’éditeur. Pour plus d’informations, consultez [création d’une Extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
## <a name="defining-the-glyph"></a>Définition du glyphe  
 Définir un glyphe en implémentant le <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> interface.  
  
#### <a name="to-define-the-glyph"></a>Pour définir le glyphe  
  
1.  Ajoutez un fichier de classe et nommez-le `TodoGlyphFactory`.  
  
2.  Ajoutez le code suivant à l’aide de déclarations.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#1)]
     [!code-vb[VSSDKTodoGlyphTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#1)]  
  
3.  Ajoutez une classe nommée `TodoGlyphFactory` qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#2)]
     [!code-vb[VSSDKTodoGlyphTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#2)]  
  
4.  Ajoutez un champ privé qui définit les dimensions du glyphe.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#3)]
     [!code-vb[VSSDKTodoGlyphTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#3)]  
  
5.  Implémentez `GenerateGlyph` en définissant l’élément d’interface (UI) glyphe. `TodoTag` est défini plus loin dans cette procédure pas à pas.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#4)]
     [!code-vb[VSSDKTodoGlyphTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#4)]  
  
6.  Ajoutez une classe nommée `TodoGlyphFactoryProvider` qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Exporter cette classe avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de « TodoGlyph », un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> d’après VsTextMarker, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « code » et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#5)]
     [!code-vb[VSSDKTodoGlyphTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#5)]  
  
7.  Implémentez le <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> méthode en instanciant le `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#6)]
     [!code-vb[VSSDKTodoGlyphTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#6)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Définition d’une balise de tâches et de la balise  
 Définir la relation entre l’élément d’interface utilisateur que vous avez défini dans les étapes précédentes et la marge des indicateurs en créant un type de balise et une balise et en exportant à l’aide d’un fournisseur de baliseur de.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Pour définir une balise de tâches et de la balise  
  
1.  Ajoutez un nouveau fichier de classe au projet et nommez-le `TodoTagger`.  
  
2.  Ajoutez les importations ci-après.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#7)]
     [!code-vb[VSSDKTodoGlyphTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#7)]  
  
3.  Ajoutez une classe nommée `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#8)]
     [!code-vb[VSSDKTodoGlyphTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#8)]  
  
4.  Modifiez la classe nommée `TodoTagger` qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de type `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#9)]
     [!code-vb[VSSDKTodoGlyphTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#9)]  
  
5.  Pour le `TodoTagger` (classe), ajouter des champs privés pour un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> et pour le texte à rechercher dans la classification s’étend.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#10)]
     [!code-vb[VSSDKTodoGlyphTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#10)]  
  
6.  Ajoutez un constructeur qui définit le classifieur.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#11)]
     [!code-vb[VSSDKTodoGlyphTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#11)]  
  
7.  Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> méthode en recherchant la classification de tous les étendues dont les noms incluent le mot « commentaire » et dont le texte contient le texte de recherche. Chaque fois que le texte recherché est trouvé, revenir génèrent un nouveau <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> de type `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#12)]
     [!code-vb[VSSDKTodoGlyphTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#12)]  
  
8.  Déclarez un `TagsChanged` événement.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#13)]
     [!code-vb[VSSDKTodoGlyphTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#13)]  
  
9. Ajoutez une classe nommée `TodoTaggerProvider` qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>et exportez-le avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « code » et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#14)]
     [!code-vb[VSSDKTodoGlyphTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#14)]  
  
10. Importer le <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#15)]
     [!code-vb[VSSDKTodoGlyphTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#15)]  
  
11. Implémentez le <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> méthode en instanciant le `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#16)]
     [!code-vb[VSSDKTodoGlyphTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#16)]  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
 Pour tester ce code, générez la solution TodoGlyphTest et exécutez-le dans l’instance expérimentale.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Pour générer et tester la solution TodoGlyphTest  
  
1.  Générez la solution.  
  
2.  Exécutez le projet en appuyant sur F5. Une deuxième instance de Visual Studio est instanciée.  
  
3.  Assurez-vous que la marge des indicateurs s’affiche. (Sur le **outils** menu, cliquez sur **Options**. Dans le **éditeur de texte** page, assurez-vous que l’option **marge des indicateurs** est sélectionnée.)  
  
4.  Ouvrez un fichier de code qui comporte des commentaires. Ajoutez le mot « todo » à une des sections de commentaire.  
  
5.  Un cercle bleu clair qui a un contour bleu foncé doit apparaître dans la marge des indicateurs à gauche de la fenêtre de code.
