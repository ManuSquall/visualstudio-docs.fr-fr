---
title: "Comment&#160;: rechercher et remplacer du texte dans les documents par programmation | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "documents (développement Office dans Visual Studio), rechercher"
  - "texte (développement Office dans Visual Studio), rechercher dans des documents"
  - "texte (développement Office dans Visual Studio), recherches de texte"
  - "recherches de texte, documents"
  - "recherches de texte, remplacer du texte"
ms.assetid: a66962f5-eeb9-4dc6-a70f-9039ab437a63
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Comment&#160;: rechercher et remplacer du texte dans les documents par programmation
  L'objet <xref:Microsoft.Office.Interop.Word.Find> est membre des objets <xref:Microsoft.Office.Interop.Word.Selection> et <xref:Microsoft.Office.Interop.Word.Range>, que vous pouvez utiliser indifféremment pour rechercher du texte dans des documents Microsoft Office Word.  La commande Replace est une extension de la commande Find.  
  
 Utilisez un objet <xref:Microsoft.Office.Interop.Word.Find> pour parcourir un document Microsoft Office Word et rechercher du texte, une mise en forme ou un style spécifique, et utilisez la propriété <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> pour remplacer l'un des éléments trouvés.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Utilisation d'un objet Selection  
 Quand vous utilisez un objet <xref:Microsoft.Office.Interop.Word.Selection> pour rechercher du texte, les critères de recherche que vous spécifiez s'appliquent uniquement au texte sélectionné.  Si l'objet <xref:Microsoft.Office.Interop.Word.Selection> est un point d'insertion, la recherche s'effectue dans le document.  Quand l'élément correspondant aux critères de recherche est trouvé, il est automatiquement sélectionné.  
  
 Il est important de noter que les critères <xref:Microsoft.Office.Interop.Word.Find> sont cumulatifs, ce qui signifie qu'ils sont ajoutés aux critères de recherche précédents.  Avant la recherche, effacez la mise en forme des recherches précédentes à l'aide de la méthode <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A>.  
  
#### Pour rechercher du texte à l'aide d'un objet Selection  
  
1.  Affectez une chaîne de recherche à une variable.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#68](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#68)]
     [!code-vb[Trin_VstcoreWordAutomation#68](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#68)]  
  
2.  Effacez la mise en forme des recherches précédentes.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#69](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#69)]
     [!code-vb[Trin_VstcoreWordAutomation#69](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#69)]  
  
3.  Exécutez la recherche et affichez une boîte de message avec les résultats.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#70](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#70)]
     [!code-vb[Trin_VstcoreWordAutomation#70](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#70)]  
  
 L'exemple suivant montre la méthode complète.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#67](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#67)]
 [!code-vb[Trin_VstcoreWordAutomation#67](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#67)]  
  
## Utilisation d'un objet Range  
 L'utilisation d'un objet <xref:Microsoft.Office.Interop.Word.Range> vous permet de rechercher du texte sans rien afficher dans l'interface utilisateur.  L'objet <xref:Microsoft.Office.Interop.Word.Find> retourne **True** si du texte correspondant aux critères de recherche est trouvé, et **False** dans le cas contraire.  Il redéfinit également l'objet <xref:Microsoft.Office.Interop.Word.Range> pour qu'il corresponde aux critères de recherche si le texte est trouvé.  
  
#### Pour rechercher du texte à l'aide d'un objet Range  
  
1.  Définissez un objet <xref:Microsoft.Office.Interop.Word.Range> constitué du deuxième paragraphe du document.  
  
     L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#72](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#72)]
     [!code-vb[Trin_VstcoreWordAutomation#72](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#72)]  
  
     L'exemple de code suivant peut être utilisé dans un complément VSTO.  Cet exemple utilise le document actif.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#72)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#72)]  
  
2.  Utilisez la propriété <xref:Microsoft.Office.Interop.Word.Range.Find%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Range> pour effacer en premier lieu toutes les éventuelles options de mise en forme existantes, puis recherchez la chaîne **find me**.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#73](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#73)]
     [!code-vb[Trin_VstcoreWordAutomation#73](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#73)]  
  
3.  Affichez les résultats de la recherche dans une boîte de message, puis sélectionnez l'objet <xref:Microsoft.Office.Interop.Word.Range> pour le rendre visible.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#74](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#74)]
     [!code-vb[Trin_VstcoreWordAutomation#74](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#74)]  
  
     Si la recherche échoue, le deuxième paragraphe est sélectionné. Si elle réussit, les critères de recherche sont affichés.  
  
 L'exemple suivant montre le code complet pour une personnalisation au niveau du document.  Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisDocument` dans votre projet.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#71](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#71)]
 [!code-vb[Trin_VstcoreWordAutomation#71](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#71)]  
  
 L'exemple suivant montre le code complet pour un complément VSTO.  Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.  
  
 [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#71)]
 [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#71)]  
  
## Recherche et remplacement de texte dans des documents  
 Le code suivant effectue une recherche dans la sélection actuelle et remplace toutes les occurrences de la chaîne **find me** par la chaîne **Found**.  
  
#### Pour rechercher et remplacer du texte dans des documents  
  
1.  Ajoutez l'exemple de code suivant à la classe `ThisDocument` ou `ThisAddIn` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#75](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#75)]
     [!code-vb[Trin_VstcoreWordAutomation#75](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#75)]  
  
     La classe <xref:Microsoft.Office.Interop.Word.Find> a une méthode <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> et la classe <xref:Microsoft.Office.Interop.Word.Replacement> a également sa propre méthode <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A>.  Quand vous effectuez des opérations de recherche et remplacement, vous devez utiliser la méthode ClearFormatting des deux objets.  Si vous l'utilisez uniquement sur l'objet <xref:Microsoft.Office.Interop.Word.Find>, vous pouvez obtenir des résultats inattendus dans le texte de remplacement.  
  
2.  Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Find> pour remplacer chaque élément trouvé.  Pour spécifier les éléments à remplacer, utilisez le paramètre *Replace*.  Ce paramètre peut avoir l'une des valeurs <xref:Microsoft.Office.Interop.Word.WdReplace> suivantes :  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> remplace tous les éléments trouvés.  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> ne remplace aucun des éléments trouvés.  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> remplace le premier élément trouvé.  
  
## Voir aussi  
 [Comment : définir les options de recherche dans Word par programmation](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Comment : parcourir les éléments trouvés dans les documents par programmation](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Comment : restaurer des sélections après des recherches par programmation](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  