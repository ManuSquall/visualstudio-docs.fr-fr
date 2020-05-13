---
title: 'Procédure pas à pas : Création d’un Glyph de marge (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9588b150dd795fc2bc5e6c55d8f6e2359f609939
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697699"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Procédure pas à pas: Créer un glyphe de marge
Vous pouvez personnaliser l’apparence des marges de l’éditeur en utilisant des extensions d’éditeur personnalisées. Cette procédure pas à pas met un glyphe personnalisé sur la marge de l’indicateur chaque fois que le mot "todo" apparaît dans un commentaire de code.

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Créer un projet MEF

1. Créez un projet VSIX CMD. (Dans le dialogue du **nouveau projet,** sélectionnez **Visual C / Extensibility**, puis **VSIX Project**.) Nommez `TodoGlyphTest`la solution .

2. Ajouter un élément de projet De classificateur d’éditeur. Pour plus d’informations, voir [Créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

## <a name="define-the-glyph"></a>Décrivez le glyphe
 Définissez un glyphe <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> en exécutant l’interface.

### <a name="to-define-the-glyph"></a>Définir le glyphe

1. Ajoutez un fichier de classe et nommez-le `TodoGlyphFactory`.

2. Ajoutez le code suivant en utilisant des déclarations.

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. Ajouter une `TodoGlyphFactory` classe nommée <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>qui implémente .

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. Ajouter un champ privé qui définit les dimensions du glyphe.

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. Implémenter `GenerateGlyph` en définissant l’interface utilisateur glyph (interface utilisateur). `TodoTag`est défini plus tard dans cette procédure pas à pas.

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. Ajouter une `TodoGlyphFactoryProvider` classe nommée <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>qui implémente . Exportez cette <xref:Microsoft.VisualStudio.Utilities.NameAttribute> classe avec un de "TodoGlyph", <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de After VsTextMarker, un de "code", et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. Implémenter la <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> méthode `TodoGlyphFactory`en instantanéisant le .

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>Décrivez une étiquette Todo et un tagger
 Définissez la relation entre l’élément d’assurance-chômage que vous avez défini dans les étapes précédentes et la marge de l’indicateur. Créez un type d’étiquette et tagger et exportez-le en utilisant un fournisseur de tagger.

### <a name="to-define-a-todo-tag-and-tagger"></a>Définir une balise todo et un tagger

1. Ajoutez un nouveau fichier de classe `TodoTagger`au projet et nommez-le .

2. Ajoutez les importations suivantes.

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. Ajoutez une classe nommée `TodoTag`.

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. Modifier la `TodoTagger` classe nommée <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> qui `TodoTag`implémente le type .

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. À `TodoTagger` la classe, ajoutez <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> des champs privés pour un et pour que le texte trouve dans les travées de classification.

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. Ajouter un constructeur qui définit le classificateur.

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> méthode en trouvant toutes les durées de classification dont les noms incluent le mot «commentaire» et dont le texte comprend le texte de recherche. Chaque fois que le texte de <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> recherche `TodoTag`est trouvé, redévenez un nouveau type .

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. Déclarez `TagsChanged` un événement.

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. Ajoutez une `TodoTaggerProvider` classe nommée <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>qui implémente, et exportez-la avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «code» et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. Importer <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>le .

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. Implémenter la <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> méthode `TodoTagger`en instantanéisant le .

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>Construire et tester le code
 Pour tester ce code, créez la solution TodoGlyphTest et exécutez-la dans l’instance expérimentale.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Construire et tester la solution TodoGlyphTest

1. Générez la solution.

2. Exécuter le projet en appuyant sur **F5**. Une deuxième instance de Visual Studio commence.

3. Assurez-vous que la marge de l’indicateur se manifeste. (Sur le menu **Outils,** cliquez sur **Options**. Sur la page **de l’éditeur de texte,** assurez-vous que **la marge d’indicateur** est sélectionnée.)

4. Ouvrez un fichier de code qui a des commentaires. Ajoutez le mot "todo" à l’une des sections de commentaires.

5. Un cercle bleu clair avec un contour bleu foncé apparaît dans la marge de l’indicateur à gauche de la fenêtre de code.
