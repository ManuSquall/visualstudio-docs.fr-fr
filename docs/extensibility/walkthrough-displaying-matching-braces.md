---
title: "Proc&#233;dure pas &#224; pas&#160;: Affichage des accolades correspondantes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), nouvelles - accolades correspondantes"
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# Proc&#233;dure pas &#224; pas&#160;: Affichage des accolades correspondantes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez implémenter des fonctionnalités reposant sur le langage comme accolades correspondantes en définissant les accolades à faire correspondre, puis en ajoutant une balise de marqueur de texte pour les accolades correspondantes lorsque le point d’insertion se trouve sur un des accolades. Vous pouvez définir des accolades dans le contexte d’une langue, vous pouvez définir votre propre type de contenu et d’extension de nom fichier et appliquer les balises à uniquement ce type, ou vous pouvez appliquer des balises à un type de contenu existant \(par exemple, « texte »\). La procédure suivante indique comment appliquer des accolades correspondantes des balises pour le type de contenu « texte ».  
  
## Composants requis  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Création d’un projet Managed Extensibility Framework \(MEF\)  
  
#### Pour créer un projet MEF  
  
1.  Créez un projet Classifieur d’éditeur. Nommez la solution `BraceMatchingTest`.  
  
2.  Ajouter un modèle d’élément éditeur classifieur au projet. Pour plus d'informations, consultez [Création d'une Extension avec un éditeur de modèle d'élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
## L’implémentation d’une accolade de correspondance de balise  
 Pour obtenir une accolade mise en surbrillance effet semblable à celui qui est utilisé dans Visual Studio, vous pouvez implémenter une balise de type <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Le code suivant montre comment définir la balise de paires d’accolade à tous les niveaux d’imbrication. Dans cet exemple, l’accolade paires \[\]. \[\] et {} sont définies dans le constructeur de la balise, mais dans une implémentation complète du langage les paires d’accolade pertinentes seraient définies dans la spécification du langage.  
  
#### Pour implémenter une accolade de correspondance de balise  
  
1.  Ajoutez un fichier de classe et nommez\-la accolade correspondante.  
  
2.  Importez les espaces de noms suivant.  
  
     [!code-cs[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  Définissez une classe `BraceMatchingTagger` qui hérite de <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de type <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-cs[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  Ajouter des propriétés pour l’affichage de texte, la mémoire tampon source et le point d’instantané en cours et également un ensemble de paires d’accolades.  
  
     [!code-cs[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  Dans le constructeur de la balise, définissez les propriétés et s’y abonner les événements de modification de vue <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> et <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. Dans cet exemple, à des fins d’illustration, les paires correspondantes sont également définies dans le constructeur.  
  
     [!code-cs[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  Dans le cadre de la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implémentation, déclarez un événement TagsChanged.  
  
     [!code-cs[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  Les gestionnaires d’événements mettre à jour l’emplacement du signe insertion de la `CurrentChar` propriété et déclencher l’événement TagsChanged.  
  
     [!code-cs[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> méthode pour faire correspondre une accolade soit lorsque le caractère actuel est une accolade ouvrante ou lorsque le caractère précédent est une accolade fermante, comme dans Visual Studio. Lorsque la correspondance est trouvée, cette méthode instancie deux balises, une pour l’accolade ouvrante et une pour l’accolade fermante.  
  
     [!code-cs[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. Les méthodes privées suivantes rechercher l’accolade correspondante n’importe quel niveau d’imbrication. La première méthode recherche le caractère de fermeture qui correspond au caractère ouvert :  
  
     [!code-cs[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. La méthode d’assistance suivante recherche le caractère ouvert qui correspond à un caractère de fermeture :  
  
     [!code-cs[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## L’implémentation d’une accolade de correspondance du fournisseur de balise  
 En plus d’implémenter une balise, vous devez également implémenter et exporter un fournisseur de balise. Dans ce cas, le type de contenu du fournisseur est « text ». Cela signifie que les accolades correspondantes apparaissent dans tous les types de fichiers texte, mais une implémentation plus complète s’appliquerait accolades correspondantes uniquement à un type de contenu spécifique.  
  
#### Pour implémenter un fournisseur de balise accolade correspondante  
  
1.  Déclarer un fournisseur de balise qui hérite de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, nommez\-le BraceMatchingTaggerProvider et l’exporter avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « text » et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-cs[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> méthode pour instancier un BraceMatchingTagger.  
  
     [!code-cs[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## Création et test du code  
 Pour tester ce code, générez la solution BraceMatchingTest et exécutez\-le dans l’instance expérimentale.  
  
#### Pour générer et tester des solutions de BraceMatchingTest  
  
1.  Générez la solution.  
  
2.  Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
3.  Créez un fichier texte et tapez du texte qui inclut des accolades correspondantes.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Lorsque vous placez le point d’insertion avant une accolade ouvrante, que les accolades et l’accolade de fermeture correspondante doit être sélectionné. Lorsque vous positionnez le curseur juste après l’accolade fermante, cette accolade et l’accolade ouvrante correspondante doit être mis en surbrillance.  
  
## Voir aussi  
 [Procédure pas à pas : Liaison d'un Type de contenu à une Extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)