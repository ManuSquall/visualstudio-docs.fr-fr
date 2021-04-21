---
title: Rechercher et remplacer du texte dans des documents par programmation
description: Découvrez comment vous pouvez utiliser Visual Studio pour rechercher et remplacer du texte dans un document Microsoft Word par programmation.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], searching
- text searches, replacing text
- text searches, documents
- text [Office development in Visual Studio], searching in documents
- text [Office development in Visual Studio], text searches
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0f2fc5bbfabbe2672ae59c55734a5cf57fc84318
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825158"
---
# <a name="how-to-programmatically-search-for-and-replace-text-in-documents"></a>Comment : Rechercher et remplacer du texte dans des documents par programmation
  L'objet <xref:Microsoft.Office.Interop.Word.Find> est membre des objets <xref:Microsoft.Office.Interop.Word.Selection> et <xref:Microsoft.Office.Interop.Word.Range>, que vous pouvez utiliser indifféremment pour rechercher du texte dans des documents Microsoft Office Word. La commande Replace est une extension de la commande Find.

 Utilisez un objet <xref:Microsoft.Office.Interop.Word.Find> pour parcourir un document Microsoft Office Word et rechercher du texte, une mise en forme ou un style spécifique, et utilisez la propriété <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> pour remplacer l'un des éléments trouvés.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-a-selection-object"></a>Utiliser un objet Selection
 Quand vous utilisez un objet <xref:Microsoft.Office.Interop.Word.Selection> pour rechercher du texte, les critères de recherche que vous spécifiez s'appliquent uniquement au texte sélectionné. Si l'objet <xref:Microsoft.Office.Interop.Word.Selection> est un point d'insertion, la recherche s'effectue dans le document. Quand l'élément correspondant aux critères de recherche est trouvé, il est automatiquement sélectionné.

 Il est important de noter que les critères <xref:Microsoft.Office.Interop.Word.Find> sont cumulatifs, ce qui signifie qu'ils sont ajoutés aux critères de recherche précédents. Avant la recherche, effacez la mise en forme des recherches précédentes à l'aide de la méthode <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A>.

### <a name="to-find-text-using-a-selection-object"></a>Pour rechercher du texte à l'aide d'un objet Selection

1. Affectez une chaîne de recherche à une variable.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet68":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet68":::

2. Effacez la mise en forme des recherches précédentes.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet69":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet69":::

3. Exécutez la recherche et affichez une boîte de message avec les résultats.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet70":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet70":::

   L'exemple suivant montre la méthode complète.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet67":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet67":::

## <a name="use-a-range-object"></a>Utilisation d’un objet Range
 L'utilisation d'un objet <xref:Microsoft.Office.Interop.Word.Range> vous permet de rechercher du texte sans rien afficher dans l'interface utilisateur. L' <xref:Microsoft.Office.Interop.Word.Find> objet retourne la **valeur true** si le texte trouvé correspond aux critères de recherche et la **valeur false** dans le cas contraire. Il redéfinit également l'objet <xref:Microsoft.Office.Interop.Word.Range> pour qu'il corresponde aux critères de recherche si le texte est trouvé.

### <a name="to-find-text-using-a-range-object"></a>Pour rechercher du texte à l'aide d'un objet Range

1. Définissez un objet <xref:Microsoft.Office.Interop.Word.Range> constitué du deuxième paragraphe du document.

    L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet72":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet72":::

    L'exemple de code suivant peut être utilisé dans un complément VSTO. Cet exemple utilise le document actif.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet72":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet72":::

2. À l’aide <xref:Microsoft.Office.Interop.Word.Range.Find%2A> de la propriété de l' <xref:Microsoft.Office.Interop.Word.Range> objet, supprimez d’abord toutes les options de mise en forme existantes, puis recherchez la chaîne **Find me**.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet73":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet73":::

3. Affichez les résultats de la recherche dans une boîte de message, puis sélectionnez l'objet <xref:Microsoft.Office.Interop.Word.Range> pour le rendre visible.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet74":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet74":::

    Si la recherche échoue, le deuxième paragraphe est sélectionné. Si elle réussit, les critères de recherche sont affichés.

   L'exemple suivant montre le code complet pour une personnalisation au niveau du document. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisDocument` dans votre projet.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet71":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet71":::

   L'exemple suivant montre le code complet pour un complément VSTO. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet71":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet71":::

## <a name="search-for-and-replace-text-in-documents"></a>Rechercher et remplacer du texte dans des documents
 Le code suivant effectue une recherche dans la sélection actuelle et remplace toutes les occurrences de la chaîne **Rechercher** par la chaîne **trouvée**.

### <a name="to-search-for-and-replace-text-in-documents"></a>Pour rechercher et remplacer du texte dans des documents

1. Ajoutez l'exemple de code suivant à la classe `ThisDocument` ou `ThisAddIn` dans votre projet.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet75":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet75":::

     La classe <xref:Microsoft.Office.Interop.Word.Find> a une méthode <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> et la classe <xref:Microsoft.Office.Interop.Word.Replacement> a également sa propre méthode <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A>. Lorsque vous effectuez des opérations de recherche et de remplacement, vous devez utiliser la méthode ClearFormatting des deux objets. Si vous l'utilisez uniquement sur l'objet <xref:Microsoft.Office.Interop.Word.Find>, vous pouvez obtenir des résultats inattendus dans le texte de remplacement.

2. Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Find> pour remplacer chaque élément trouvé. Pour spécifier les éléments à remplacer, utilisez le paramètre *Replace* . Ce paramètre peut avoir l'une des valeurs <xref:Microsoft.Office.Interop.Word.WdReplace> suivantes :

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> remplace tous les éléments trouvés.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> ne remplace aucun des éléments trouvés.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> remplace le premier élément trouvé.

## <a name="see-also"></a>Voir aussi
- [Comment : définir des options de recherche dans Word par programmation](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Comment : parcourir les éléments trouvés dans les documents par programmation](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Comment : restaurer des sélections après des recherches par programmation](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
