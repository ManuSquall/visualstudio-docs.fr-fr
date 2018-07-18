---
title: 'Procédure pas à pas : Création d’un glyphe de marge | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 811985ef45fb43b08b771f2bc417a512c290726c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142628"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>Procédure pas à pas : Création d’un glyphe de marge
Vous pouvez personnaliser l’apparence des marges d’éditeur à l’aide des extensions de l’éditeur personnalisé. Cette procédure pas à pas place un glyphe personnalisé sur la marge des indicateurs à chaque fois que le mot « todo » s’affiche dans un commentaire de code.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Création d’un projet MEF  
  
1.  Créez un projet VSIX c#. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual c# / extensibilité**, puis **projet VSIX**.) Nommez la solution `TodoGlyphTest`.  
  
2.  Ajouter un élément de projet classifieur d’éditeur. Pour plus d’informations, consultez [création d’une Extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
## <a name="defining-the-glyph"></a>Définir le glyphe  
 Définir un glyphe en implémentant le <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> interface.  
  
#### <a name="to-define-the-glyph"></a>Pour définir le glyphe  
  
1.  Ajoutez un fichier de classe et nommez-le `TodoGlyphFactory`.  
  
2.  Ajoutez le code suivant à l’aide des déclarations.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  Ajoutez une classe nommée `TodoGlyphFactory` qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  Ajoutez un champ privé qui définit les dimensions du glyphe.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  Implémentez `GenerateGlyph` en définissant l’élément d’interface utilisateur utilisateur glyphe. `TodoTag` est défini plus loin dans cette procédure pas à pas.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  Ajoutez une classe nommée `TodoGlyphFactoryProvider` qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Exporter cette classe avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de « TodoGlyph », un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> d’après VsTextMarker, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « code » et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  Implémentez la <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> méthode en instanciant le `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Définition d’une balise de tâches et de la balise  
 Définir la relation entre l’élément d’interface utilisateur que vous avez définie dans les étapes précédentes et la marge des indicateurs en créant un type de balise et la balise et exportant à l’aide d’un fournisseur de baliseur.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Pour définir une balise de tâches et de la balise  
  
1.  Ajouter un nouveau fichier de classe au projet et nommez-le `TodoTagger`.  
  
2.  Ajoutez les importations suivantes.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  Ajoutez une classe nommée `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  Modifiez la classe nommée `TodoTagger` qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de type `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  Pour le `TodoTagger` (classe), ajoutez des champs privés pour un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> et pour le texte à rechercher dans la classification s’étend.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  Ajoutez un constructeur qui définit le classifieur.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> méthode en recherchant la classification de tous les couvre dont les noms incluent le mot « commentaire » et dont le texte contient le texte de recherche. Chaque fois que le texte de recherche est trouvé, revenir génère un nouveau <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> de type `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  Déclarez un `TagsChanged` événement.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. Ajoutez une classe nommée `TodoTaggerProvider` qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>et l’exporter avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « code » et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. Importer le <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> méthode en instanciant le `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
 Pour tester ce code, générez la solution TodoGlyphTest et l’exécuter dans l’instance expérimentale.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Pour générer et tester la solution TodoGlyphTest  
  
1.  Générez la solution.  
  
2.  Exécutez le projet en appuyant sur F5. Une deuxième instance de Visual Studio est instanciée.  
  
3.  Assurez-vous que la marge des indicateurs s’affiche. (Sur le **outils** menu, cliquez sur **Options**. Dans le **éditeur de texte** , assurez-vous que **marge des indicateurs** est sélectionné.)  
  
4.  Ouvrez un fichier de code qui a des commentaires. Ajoutez le mot « todo » à une des sections de commentaire.  
  
5.  Un cercle bleu clair qui a un contour bleu foncé doit apparaître dans la marge des indicateurs à gauche de la fenêtre de code.