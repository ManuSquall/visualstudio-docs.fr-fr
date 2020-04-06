---
title: 'Procédure pas à pas : Affichage d’accolades assorties (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 107610733ab9b5c8085b3f987fa999250b453d63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697452"
---
# <a name="walkthrough-display-matching-braces"></a>Procédure pas à pas : Afficher des accolades assorties
Implémentez des fonctionnalités basées sur la langue, telles que l’appariement des accolades en définissant les accolades que vous souhaitez assortir, et en ajoutant une balise de marqueur de texte aux accolades assorties lorsque la caret est sur l’une des accolades. Vous pouvez définir les accolades dans le contexte d’une langue, définir votre propre extension de nom de fichier et le type de contenu, et appliquer les balises à ce type ou appliquer les balises à un type de contenu existant (comme "texte"). Le pas à pas suivant montre comment appliquer des balises assorties d’accolades au type de contenu « texte ».

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Créer un projet de cadre d’exténuabilité gérée (MEF)

#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF

1. Créez un projet Classifieur d’éditeur. Nommez la solution `BraceMatchingTest`.

2. Ajoutez un modèle d’élément Classificateur d’éditeur au projet. Pour plus d’informations, voir [Créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

## <a name="implement-a-brace-matching-tagger"></a>Mettre en œuvre un tagger assorti à une accolade
 Pour obtenir un effet de mise en évidence accolade qui ressemble à celui qui <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>est utilisé dans Visual Studio, vous pouvez implémenter un tagger de type . Le code suivant montre comment définir le tagger pour les paires d’accolades à n’importe quel niveau de nidification. Dans cet exemple, les paires {} d’accolades de [] et sont définies dans le constructeur de tagger, mais dans une mise en œuvre en langage complet, les paires d’accolades pertinentes seraient définies dans la spécification de la langue.

### <a name="to-implement-a-brace-matching-tagger"></a>Pour mettre en œuvre un tagger assorti d’accolade

1. Ajoutez un fichier de classe et nommez-le BraceMatching.

2. Importez les espaces nom suivants.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. Définir une `BraceMatchingTagger` classe qui <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> hérite du type <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. Ajoutez des propriétés pour la vue de texte, le tampon source, le point d’instantané actuel, et également un ensemble de paires d’accolades.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. Dans le constructeur tagger, définir les propriétés <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> et <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>abonnez-vous aux événements de changement de vue et . Dans cet exemple, à des fins d’illustration, les paires correspondantes sont également définies dans le constructeur.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. Dans le <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> cadre de la mise en œuvre, déclarez un événement TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. Les gestionnaires de l’événement mettent `CurrentChar` à jour la position actuelle de la propriété et soulèvent l’événement TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. Implémenter la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> méthode pour assortir les accolades soit lorsque le personnage actuel est un corset ouvert ou lorsque le personnage précédent est un corset proche, comme dans Visual Studio. Lorsque le match est trouvé, cette méthode instantané deux balises, l’une pour l’accolade ouverte et l’autre pour l’accolade rapprochée.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. Les méthodes privées suivantes trouvent l’accolade assortie à n’importe quel niveau de nidification. La première méthode trouve le caractère proche qui correspond au caractère ouvert :

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. La méthode d’aide suivante trouve le caractère ouvert qui correspond à un personnage proche :

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>Mettre en œuvre un fournisseur de tagger assorti
 En plus de mettre en œuvre un tagger, vous devez également implémenter et exporter un fournisseur de tagger. Dans ce cas, le type de contenu du fournisseur est "texte". Ainsi, l’appariement d’accolade apparaîtra dans tous les types de fichiers texte, mais une implémentation plus complète applique l’accolade correspondant uniquement à un type de contenu spécifique.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Pour mettre en œuvre un fournisseur de tagger assorti

1. Déclarez un fournisseur de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>tagger qui hérite de , nomt-le <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> BraceMatchingTaggerProvider, et exportez-le avec un de "texte" et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> méthode pour instantanér un BraceMatchingTagger.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>Construire et tester le code
 Pour tester ce code, créez la solution BraceMatchingTest et exécutez-la dans le cas expérimental.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>Construire et tester la solution BraceMatchingTest

1. Générez la solution.

2. Lorsque vous exécutez ce projet dans le débbugger, une deuxième instance de Visual Studio est lancée.

3. Créez un fichier texte et tapez du texte qui inclut des accolades assorties.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Lorsque vous placez la caret avant une accolade ouverte, cette accolade et l’accolade rapprochée correspondant doivent être mis en évidence. Lorsque vous placez le curseur juste après l’accolade rapprochée, cette accolade et l’attelle ouverte assortie doivent être mis en évidence.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : liez un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
