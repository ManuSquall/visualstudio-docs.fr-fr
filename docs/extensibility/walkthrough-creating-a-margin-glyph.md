---
title: 'Procédure pas à pas : création d’un glyphe de marge | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b94ab61f56d74537758c189adc9c104516f67f92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905054"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Procédure pas à pas : créer un glyphe de marge
Vous pouvez personnaliser l’apparence des marges de l’éditeur à l’aide des extensions personnalisées de l’éditeur. Cette procédure pas à pas place un glyphe personnalisé sur la marge des indicateurs chaque fois que le mot « todo » apparaît dans un commentaire de code.

## <a name="prerequisites"></a>Prérequis
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Créer un projet MEF

1. Créez un projet VSIX C#. (Dans la boîte de dialogue **nouveau projet** , sélectionnez **Visual C#/extensibilité**, puis **projet VSIX**.) Nommez la solution `TodoGlyphTest` .

2. Ajoutez un élément de projet classifieur de l’éditeur. Pour plus d’informations, consultez [créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

## <a name="define-the-glyph"></a>Définir le glyphe
 Définissez un glyphe en exécutant l' <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> interface.

### <a name="to-define-the-glyph"></a>Pour définir le glyphe

1. Ajoutez un fichier de classe et nommez-le `TodoGlyphFactory`.

2. Ajoutez le code suivant à l’aide de déclarations.

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. Ajoutez une classe nommée `TodoGlyphFactory` qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. Ajoutez un champ privé qui définit les dimensions du glyphe.

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. Implémentez `GenerateGlyph` en définissant l’élément d’interface utilisateur du glyphe. `TodoTag` est défini plus loin dans cette procédure pas à pas.

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. Ajoutez une classe nommée `TodoGlyphFactoryProvider` qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Exportez cette classe avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de « TodoGlyph », un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de après VsTextMarker, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « code » et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. Implémentez la <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> méthode en instanciant le `TodoGlyphFactory` .

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>Définir une balise TODO et une balise
 Définissez la relation entre l’élément d’interface utilisateur que vous avez défini dans les étapes précédentes et la marge des indicateurs. Créez un type et une balise tag et exportez-le à l’aide d’un fournisseur de balises.

### <a name="to-define-a-todo-tag-and-tagger"></a>Pour définir une balise TODO et une balise

1. Ajoutez un nouveau fichier de classe au projet et nommez-le `TodoTagger` .

2. Ajoutez les importations suivantes.

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. Ajoutez une classe nommée `TodoTag`.

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. Modifiez la classe nommée `TodoTagger` qui implémente le <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> type `TodoTag` .

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. Pour la `TodoTagger` classe, ajoutez des champs privés pour un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> et pour le texte à rechercher dans les étendues de classification.

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. Ajoutez un constructeur qui définit le classifieur.

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> méthode en recherchant toutes les étendues de classification dont les noms incluent le mot « comment » et dont le texte inclut le texte recherché. Chaque fois que le texte recherché est trouvé, reproduisez un nouveau <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> de type `TodoTag` .

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. Déclarez un `TagsChanged` événement.

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. Ajoutez une classe nommée `TodoTaggerProvider` qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> et exportez-la avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « code » et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. Importez le <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> méthode en instanciant le `TodoTagger` .

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>Générer et tester le code
 Pour tester ce code, générez la solution TodoGlyphTest et exécutez-la dans l’instance expérimentale.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Pour générer et tester la solution TodoGlyphTest

1. Générez la solution.

2. Exécutez le projet en appuyant sur **F5**. Une deuxième instance de Visual Studio démarre.

3. Assurez-vous que la marge des indicateurs est affichée. (Dans le menu **Outils** , cliquez sur **options**. Sur la page **éditeur de texte** , assurez-vous que la marge des **indicateurs** est sélectionnée.)

4. Ouvrez un fichier de code qui contient des commentaires. Ajoutez le mot « todo » à l’une des sections de commentaire.

5. Un cercle bleu clair avec un contour bleu foncé apparaît dans la marge des indicateurs à gauche de la fenêtre de code.
