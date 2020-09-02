---
title: 'Procédure pas à pas : affichage des accolades correspondantes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caaafd0143d3b09a51518ee5f54a02b06dbf10aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165787"
---
# <a name="walkthrough-displaying-matching-braces"></a>Procédure pas à pas : affichage d’accolades correspondantes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez implémenter des fonctionnalités basées sur le langage, telles que la correspondance d’accolades, en définissant les accolades auxquelles vous souhaitez faire correspondre, puis en ajoutant une balise de marqueur de texte aux accolades correspondantes lorsque le signe insertion se trouve sur l’une des accolades. Vous pouvez définir des accolades dans le contexte d’une langue, ou vous pouvez définir votre propre extension de nom de fichier et type de contenu et appliquer les balises uniquement à ce type, ou vous pouvez appliquer les balises à un type de contenu existant (tel que « texte »). La procédure pas à pas suivante montre comment appliquer des balises correspondantes au type de contenu « text ».  
  
## <a name="prerequisites"></a>Prérequis  
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Création d’un projet Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF  
  
1. Créez un projet Classifieur d’éditeur. Nommez la solution `BraceMatchingTest`.  
  
2. Ajoutez un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [création d’une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Supprimez les fichiers de classe existants.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Implémentation d’une balise correspondant à l’accolade  
 Pour obtenir un effet de mise en surbrillance des accolades qui ressemble à celui utilisé dans Visual Studio, vous pouvez implémenter une balise de type <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> . Le code suivant montre comment définir la balise pour les paires d’accolades à n’importe quel niveau d’imbrication. Dans cet exemple, les paires d’accolades []. [], et {} sont définis dans le constructeur de balises, mais dans une implémentation de langage complète, les paires d’accolades appropriées sont définies dans la spécification du langage.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Pour implémenter une balise de correspondance d’accolades  
  
1. Ajoutez un fichier de classe et nommez-le BraceMatching.  
  
2. Importez les espaces de noms suivants.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#1)]
     [!code-vb[VSSDKBraceMatchingTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#1)]  
  
3. Définissez une classe `BraceMatchingTagger` qui hérite de <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de type <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#2)]
     [!code-vb[VSSDKBraceMatchingTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#2)]  
  
4. Ajoutez des propriétés pour l’affichage de texte, la mémoire tampon source et le point d’instantané actuel, ainsi qu’un ensemble de paires d’accolades.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#3)]
     [!code-vb[VSSDKBraceMatchingTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#3)]  
  
5. Dans le constructeur de balises, définissez les propriétés et abonnez-vous aux événements de modification d’affichage <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> et <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> . Dans cet exemple, à des fins d’illustration, les paires correspondantes sont également définies dans le constructeur.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#4)]
     [!code-vb[VSSDKBraceMatchingTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#4)]  
  
6. Dans le cadre de l' <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implémentation, déclarez un événement TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#5)]
     [!code-vb[VSSDKBraceMatchingTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#5)]  
  
7. Les gestionnaires d’événements mettent à jour l’emplacement actuel du signe insertion de la `CurrentChar` propriété et déclenchent l’événement TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#6)]
     [!code-vb[VSSDKBraceMatchingTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#6)]  
  
8. Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> méthode pour mettre en correspondance des accolades lorsque le caractère actuel est une accolade ouvrante ou lorsque le caractère précédent est une accolade fermante, comme dans Visual Studio. Lorsque la correspondance est trouvée, cette méthode instancie deux balises, une pour l’accolade ouvrante et une pour l’accolade fermante.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#7)]
     [!code-vb[VSSDKBraceMatchingTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#7)]  
  
9. Les méthodes privées suivantes recherchent l’accolade correspondante à n’importe quel niveau d’imbrication. La première méthode recherche le caractère de fermeture qui correspond au caractère ouvert :  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#8)]
     [!code-vb[VSSDKBraceMatchingTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#8)]  
  
10. La méthode d’assistance suivante recherche le caractère ouvert qui correspond à un caractère de fermeture :  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#9)]
     [!code-vb[VSSDKBraceMatchingTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#9)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Implémentation d’un fournisseur de balises correspondant à l’accolade  
 Outre l’implémentation d’une balise, vous devez également implémenter et exporter un fournisseur de balises. Dans ce cas, le type de contenu du fournisseur est « Text ». Cela signifie que la correspondance des accolades apparaîtra dans tous les types de fichiers texte, mais une implémentation plus complète appliquerait une correspondance d’accolades uniquement à un type de contenu spécifique.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Pour implémenter un fournisseur de balises correspondant à l’accolade  
  
1. Déclarez un fournisseur de balises qui hérite de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , nommez-le BraceMatchingTaggerProvider, puis exportez-le avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « Text » et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#10)]
     [!code-vb[VSSDKBraceMatchingTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#10)]  
  
2. Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> méthode pour instancier un BraceMatchingTagger.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#11)]
     [!code-vb[VSSDKBraceMatchingTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#11)]  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
 Pour tester ce code, générez la solution BraceMatchingTest et exécutez-la dans l’instance expérimentale.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Pour générer et tester la solution BraceMatchingTest  
  
1. Générez la solution.  
  
2. Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
3. Créez un fichier texte et tapez du texte qui contient des accolades correspondantes.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4. Quand vous placez le signe insertion avant une accolade ouvrante, les deux accolades et l’accolade fermante correspondante doivent être mises en surbrillance. Lorsque vous positionnez le curseur juste après l’accolade fermante, cette accolade et l’accolade ouvrante correspondante doivent être mises en surbrillance.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Liaison d’un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
