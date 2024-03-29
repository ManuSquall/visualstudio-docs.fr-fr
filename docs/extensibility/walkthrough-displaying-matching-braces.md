---
title: 'Procédure pas à pas : affichage des accolades correspondantes | Microsoft Docs'
description: Découvrez comment définir des accolades dans le contexte d’un langage, en appliquant des balises correspondantes au type de contenu texte à l’aide de cette procédure pas à pas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e4565e095c6bd8fe26f0bb72bd66d6df935ff16b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217266"
---
# <a name="walkthrough-display-matching-braces"></a>Procédure pas à pas : afficher les accolades correspondantes
Implémentez des fonctionnalités basées sur le langage, telles que la correspondance d’accolades en définissant les accolades que vous souhaitez mettre en correspondance, et en ajoutant une balise de marqueur de texte aux accolades correspondantes lorsque le signe insertion se trouve sur l’une des accolades. Vous pouvez définir des accolades dans le contexte d’un langage, définir votre propre extension de nom de fichier et type de contenu, et appliquer les balises uniquement à ce type ou appliquer les balises à un type de contenu existant (tel que « texte »). La procédure pas à pas suivante montre comment appliquer des balises correspondantes au type de contenu « text ».

## <a name="prerequisites"></a>Prérequis
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Créer un projet Managed Extensibility Framework (MEF)

#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF

1. Créez un projet Classifieur d’éditeur. Nommez la solution `BraceMatchingTest`.

2. Ajoutez un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

## <a name="implement-a-brace-matching-tagger"></a>Implémenter une balise de correspondance d’accolade
 Pour obtenir un effet de mise en surbrillance des accolades qui ressemble à celui utilisé dans Visual Studio, vous pouvez implémenter une balise de type <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> . Le code suivant montre comment définir la balise pour les paires d’accolades à n’importe quel niveau d’imbrication. Dans cet exemple, les paires d’accolades de [] et {} sont définies dans le constructeur de balises, mais dans une implémentation de langage complète, les paires d’accolades appropriées sont définies dans la spécification du langage.

### <a name="to-implement-a-brace-matching-tagger"></a>Pour implémenter une balise de correspondance d’accolades

1. Ajoutez un fichier de classe et nommez-le BraceMatching.

2. Importez les espaces de noms suivants.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet1":::

3. Définissez une classe `BraceMatchingTagger` qui hérite de <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de type <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet2":::

4. Ajoutez des propriétés pour l’affichage de texte, la mémoire tampon source, le point d’instantané actuel et un ensemble de paires d’accolades.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet3":::

5. Dans le constructeur de balises, définissez les propriétés et abonnez-vous aux événements de modification d’affichage <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> et <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> . Dans cet exemple, à des fins d’illustration, les paires correspondantes sont également définies dans le constructeur.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet4":::

6. Dans le cadre de l' <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implémentation, déclarez un événement TagsChanged.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet5":::

7. Les gestionnaires d’événements mettent à jour l’emplacement actuel du signe insertion de la `CurrentChar` propriété et déclenchent l’événement TagsChanged.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet6":::

8. Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> méthode pour mettre en correspondance des accolades lorsque le caractère actuel est une accolade ouvrante ou lorsque le caractère précédent est une accolade fermante, comme dans Visual Studio. Lorsque la correspondance est trouvée, cette méthode instancie deux balises, une pour l’accolade ouvrante et une pour l’accolade fermante.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet7":::

9. Les méthodes privées suivantes recherchent l’accolade correspondante à n’importe quel niveau d’imbrication. La première méthode recherche le caractère de fermeture qui correspond au caractère ouvert :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet8":::

10. La méthode d’assistance suivante recherche le caractère ouvert qui correspond à un caractère de fermeture :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet9":::

## <a name="implement-a-brace-matching-tagger-provider"></a>Implémenter un fournisseur de balises correspondant à l’accolade
 Outre l’implémentation d’une balise, vous devez également implémenter et exporter un fournisseur de balises. Dans ce cas, le type de contenu du fournisseur est « Text ». Par conséquent, la correspondance des accolades apparaît dans tous les types de fichiers texte, mais une implémentation plus complète applique des accolades correspondantes uniquement à un type de contenu spécifique.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Pour implémenter un fournisseur de balises correspondant à l’accolade

1. Déclarez un fournisseur de balises qui hérite de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , nommez-le BraceMatchingTaggerProvider, puis exportez-le avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « Text » et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet10":::

2. Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> méthode pour instancier un BraceMatchingTagger.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet11":::

## <a name="build-and-test-the-code"></a>Générer et tester le code
 Pour tester ce code, générez la solution BraceMatchingTest et exécutez-la dans l’instance expérimentale.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>Pour générer et tester la solution BraceMatchingTest

1. Générez la solution.

2. Quand vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est démarrée.

3. Créez un fichier texte et tapez du texte qui contient des accolades correspondantes.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Quand vous placez le signe insertion avant une accolade ouvrante, les deux accolades et l’accolade fermante correspondante doivent être mises en surbrillance. Lorsque vous positionnez le curseur juste après l’accolade fermante, cette accolade et l’accolade ouvrante correspondante doivent être mises en surbrillance.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : liaison d’un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
