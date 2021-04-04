---
title: 'Procédure pas à pas : création d’un glyphe de marge | Microsoft Docs'
description: Découvrez comment personnaliser l’apparence des marges de l’éditeur à l’aide des extensions d’éditeur personnalisées à l’aide de cette procédure pas à pas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec5eecef40220c2cf2d4e3f1ece8eb5eb763bdeb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217409"
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

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet1":::

3. Ajoutez une classe nommée `TodoGlyphFactory` qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet2":::

4. Ajoutez un champ privé qui définit les dimensions du glyphe.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet3":::

5. Implémentez `GenerateGlyph` en définissant l’élément d’interface utilisateur du glyphe. `TodoTag` est défini plus loin dans cette procédure pas à pas.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet4":::

6. Ajoutez une classe nommée `TodoGlyphFactoryProvider` qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Exportez cette classe avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de « TodoGlyph », un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de après VsTextMarker, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « code » et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet5":::

7. Implémentez la <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> méthode en instanciant le `TodoGlyphFactory` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet6":::

## <a name="define-a-todo-tag-and-tagger"></a>Définir une balise TODO et une balise
 Définissez la relation entre l’élément d’interface utilisateur que vous avez défini dans les étapes précédentes et la marge des indicateurs. Créez un type et une balise tag et exportez-le à l’aide d’un fournisseur de balises.

### <a name="to-define-a-todo-tag-and-tagger"></a>Pour définir une balise TODO et une balise

1. Ajoutez un nouveau fichier de classe au projet et nommez-le `TodoTagger` .

2. Ajoutez les importations suivantes.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet7":::

3. Ajoutez une classe nommée `TodoTag`.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet8":::

4. Modifiez la classe nommée `TodoTagger` qui implémente le <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> type `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet9":::

5. Pour la `TodoTagger` classe, ajoutez des champs privés pour un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> et pour le texte à rechercher dans les étendues de classification.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet10":::

6. Ajoutez un constructeur qui définit le classifieur.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet11":::

7. Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> méthode en recherchant toutes les étendues de classification dont les noms incluent le mot « comment » et dont le texte inclut le texte recherché. Chaque fois que le texte recherché est trouvé, reproduisez un nouveau <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> de type `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet12":::

8. Déclarez un `TagsChanged` événement.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet13":::

9. Ajoutez une classe nommée `TodoTaggerProvider` qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> et exportez-la avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « code » et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet14":::

10. Importez le <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet15":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet15":::

11. Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> méthode en instanciant le `TodoTagger` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet16":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet16":::

## <a name="build-and-test-the-code"></a>Générer et tester le code
 Pour tester ce code, générez la solution TodoGlyphTest et exécutez-la dans l’instance expérimentale.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Pour générer et tester la solution TodoGlyphTest

1. Générez la solution.

2. Exécutez le projet en appuyant sur **F5**. Une deuxième instance de Visual Studio démarre.

3. Assurez-vous que la marge des indicateurs est affichée. (Dans le menu **Outils** , cliquez sur **options**. Sur la page **éditeur de texte** , assurez-vous que la marge des **indicateurs** est sélectionnée.)

4. Ouvrez un fichier de code qui contient des commentaires. Ajoutez le mot « todo » à l’une des sections de commentaire.

5. Un cercle bleu clair avec un contour bleu foncé apparaît dans la marge des indicateurs à gauche de la fenêtre de code.
