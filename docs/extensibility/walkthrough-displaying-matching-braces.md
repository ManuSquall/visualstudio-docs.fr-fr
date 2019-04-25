---
title: 'Procédure pas à pas : Affichage d’accolades correspondantes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae1b0f45d119b759d6618630a65353eff4415c78
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60086531"
---
# <a name="walkthrough-display-matching-braces"></a>Procédure pas à pas : Afficher les accolades correspondantes
Implémenter des fonctionnalités en fonction de langage, par exemple, les accolades correspondantes en définissant les accolades que vous souhaitez faire correspondre et en ajoutant une balise de marqueur de texte pour les accolades correspondantes lorsque le signe insertion se trouve sur un des accolades. Vous pouvez définir des accolades dans le contexte d’une langue, définir votre propre extension de nom de fichier et le type de contenu et appliquer les balises pour juste que tapez, ou appliquent les balises à un type de contenu existant (par exemple, « text »). La procédure suivante montre comment appliquer des balises pour le type de contenu « texte » de la correspondance des accolades.

## <a name="prerequisites"></a>Prérequis
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Créer un projet Managed Extensibility Framework (MEF)

#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF

1. Créez un projet Classifieur d’éditeur. Nommez la solution `BraceMatchingTest`.

2. Ajouter un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [créer une extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

## <a name="implement-a-brace-matching-tagger"></a>Implémenter une balise de la correspondance des accolades
 Pour obtenir une accolade mise en surbrillance d’effet qui ressemble à celui qui est utilisé dans Visual Studio, vous pouvez implémenter une balise de type <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Le code suivant montre comment définir la balise pour les paires d’accolades à tous les niveaux d’imbrication. Dans cet exemple, les paires d’accolades de [] et {} sont définis dans le constructeur de balise, mais dans une implémentation complète du langage, l’accolade pertinentes paires seraient définies dans la spécification du langage.

### <a name="to-implement-a-brace-matching-tagger"></a>Pour implémenter une balise de la correspondance des accolades

1. Ajoutez un fichier de classe et nommez-le accolade correspondante.

2. Importez les espaces de noms suivants.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. Définissez une classe `BraceMatchingTagger` qui hérite de <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de type <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. Ajouter des propriétés pour l’affichage de texte, la mémoire tampon source, le point d’instantané en cours et également un ensemble de paires d’accolades.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. Dans le constructeur de la balise, définissez les propriétés et vous abonner aux événements de changement de vue <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> et <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. Dans cet exemple, à des fins d’illustration, les paires correspondantes sont également définies dans le constructeur.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. Dans le cadre de la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implémentation, déclarez un événement TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. Les gestionnaires d’événements mettre à jour la position actuelle du signe insertion de la `CurrentChar` propriété et déclencher l’événement TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> méthode pour faire correspondre une accolade soit lorsque le caractère actuel est une accolade ouvrante ou lorsque le caractère précédent est une accolade fermante, comme dans Visual Studio. Lorsque la correspondance est trouvée, cette méthode instancie deux balises, une pour l’accolade ouvrante et une pour l’accolade fermante.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. Les méthodes privées suivantes rechercher l’accolade correspondante à tous les niveaux d’imbrication. La première méthode recherche le caractère de fermeture qui correspond au caractère ouvert :

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. La méthode d’assistance suivante recherche le caractère ouvert qui correspond à un caractère de fermeture :

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>Implémenter un fournisseur de baliseur accolade correspondante
 En plus d’implémenter une balise, vous devez également implémenter et exporter un fournisseur de baliseur. Dans ce cas, le type de contenu du fournisseur est « text ». Par conséquent, les accolades correspondantes s’affiche dans tous les types de fichiers texte, mais une implémentation plus complète s’applique uniquement à un type de contenu spécifique la correspondance des accolades.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Pour implémenter un fournisseur de baliseur accolade correspondante

1. Déclarer un fournisseur de baliseur qui hérite de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, nommez-le BraceMatchingTaggerProvider et exportez-le avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « text » et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> méthode pour instancier un BraceMatchingTagger.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>Générer et tester le code
 Pour tester ce code, générez la solution BraceMatchingTest et exécutez-le dans l’instance expérimentale.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>Pour générer et tester la solution de BraceMatchingTest

1. Générez la solution.

2. Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est démarrée.

3. Créez un fichier texte et tapez du texte qui inclut des accolades correspondantes.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Lorsque vous placez le point d’insertion avant une accolade ouvrante, cette accolade et l’accolade de fermeture correspondante doit être mis en surbrillance. Lorsque vous positionnez le curseur juste après l’accolade fermante, cette accolade et l’accolade ouvrante correspondante doit être mis en surbrillance.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : Lier un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)