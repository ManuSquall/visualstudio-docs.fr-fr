---
title: "Comment&#160;: exclure les marques de paragraphe lors de la cr&#233;ation de plages par programmation | Microsoft Docs"
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
  - "documents (développement Office dans Visual Studio), exclusion de paragraphes"
  - "plages, exclusion des marques de paragraphe dans Word"
  - "documents (développement Office dans Visual Studio), marques de paragraphe"
  - "paragraphes, contrôle de la structure"
ms.assetid: 6d563834-34bd-4462-a556-4339d9277eee
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# Comment&#160;: exclure les marques de paragraphe lors de la cr&#233;ation de plages par programmation
  Chaque fois que vous créez un objet <xref:Microsoft.Office.Interop.Word.Range> basé sur un paragraphe, tous les caractères non imprimables, comme les marques de paragraphe, sont inclus dans la plage. Vous pouvez insérer le texte d’un paragraphe source dans un paragraphe de destination. Si vous ne voulez pas fractionner le paragraphe de destination en paragraphes distincts, alors vous devez d’abord supprimer la marque de paragraphe du paragraphe source. De plus, dans la mesure où des informations de mise en forme sont stockées au sein de la marque de paragraphe, vous ne voulez peut\-être pas l’inclure quand vous insérez la plage dans un paragraphe existant.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 L’exemple de procédure suivant déclare deux variables de chaîne, extrait le contenu des premier et deuxième paragraphes du document actif, puis intervertit leur contenu. L’exemple illustre ensuite la suppression de la marque de paragraphe de la plage à l’aide de la méthode <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> et l’insertion du texte à l’intérieur du paragraphe.  
  
### Pour contrôler la structure de paragraphe lors de l’insertion de texte  
  
1.  Créez deux variables de plage pour les premier et deuxième paragraphes, puis extrayez leur contenu à l’aide de la propriété <xref:Microsoft.Office.Interop.Word.Range.Text%2A>.  
  
     L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#27)]
     [!code-vb[Trin_VstcoreWordAutomation#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#27)]  
  
     L’exemple de code suivant peut être utilisé dans un complément VSTO au niveau de l’application. Ce code utilise le document actif.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#27)]  
  
2.  Affectez la propriété <xref:Microsoft.Office.Interop.Word.Range.Text%2A>, en intervertissant le texte des deux paragraphes.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#28)]
     [!code-vb[Trin_VstcoreWordAutomation#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#28)]  
  
3.  Sélectionnez chaque plage une par une, puis effectuez une pause pour afficher les résultats dans une boîte de message.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#29)]
     [!code-vb[Trin_VstcoreWordAutomation#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#29)]  
  
4.  Ajustez `firstRange` à l’aide de la méthode <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> pour que la marque de paragraphe ne fasse plus partie de `firstRange`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreWordAutomation#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#30)]  
  
5.  Remplacez le reste du texte dans le premier paragraphe, en affectant une nouvelle chaîne à la propriété <xref:Microsoft.Office.Interop.Word.Range.Text%2A> de la plage.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreWordAutomation#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#31)]  
  
6.  Remplacez le texte dans `secondRange`, en incluant la marque de paragraphe.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#32)]
     [!code-vb[Trin_VstcoreWordAutomation#32](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#32)]  
  
7.  Sélectionnez `firstRange` et effectuez une pause pour afficher les résultats dans une boîte de message, puis procédez de la même façon avec `secondRange`.  
  
     Étant donné que `firstRange` a été redéfini pour exclure la marque de paragraphe, la mise en forme d’origine du paragraphe est conservée. En revanche, une phrase a été insérée à la place de la marque de paragraphe dans `secondRange`, supprimant ainsi le paragraphe distinct.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#33)]
     [!code-vb[Trin_VstcoreWordAutomation#33](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#33)]  
  
     Le contenu d’origine des deux plages a été enregistré sous forme de chaînes, donc vous pouvez rétablir le document à son état d’origine.  
  
8.  Réajustez `firstRange` pour inclure la marque de paragraphe à l’aide de la méthode <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> pour une seule position de caractère.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#34](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreWordAutomation#34](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#34)]  
  
9. Supprimez `secondRange`. Cette opération rétablit le paragraphe trois à sa position d’origine.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#35](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#35)]
     [!code-vb[Trin_VstcoreWordAutomation#35](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#35)]  
  
10. Rétablissez le texte du paragraphe d’origine dans `firstRange`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#36](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#36)]
     [!code-vb[Trin_VstcoreWordAutomation#36](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#36)]  
  
11. Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Range> pour insérer le contenu du paragraphe deux d’origine après `firstRange`, puis sélectionnez `firstRange`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#37](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#37)]
     [!code-vb[Trin_VstcoreWordAutomation#37](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#37)]  
  
## Exemple de personnalisation au niveau du document  
  
#### Pour contrôler la structure de paragraphe lors de l’insertion de texte dans des personnalisations au niveau du document  
  
1.  L’exemple suivant montre la méthode complète d’une personnalisation au niveau du document. Pour utiliser ce code, exécutez\-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#26)]
     [!code-vb[Trin_VstcoreWordAutomation#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#26)]  
  
## Exemple de complément VSTO  
  
#### Pour contrôler la structure de paragraphe lors de l’insertion de texte dans un complément VSTO  
  
1.  L’exemple suivant montre la méthode complète d’un complément VSTO. Pour utiliser ce code, exécutez\-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#26)]  
  
## Voir aussi  
 [Comment : étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Comment : réduire des plages ou des sélections dans des documents par programmation](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Comment : insérer du texte dans les documents Word par programmation](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Comment : réinitialiser des plages dans les documents Word par programmation](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  