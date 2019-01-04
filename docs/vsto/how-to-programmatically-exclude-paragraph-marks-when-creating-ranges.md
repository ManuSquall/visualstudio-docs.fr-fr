---
title: 'Procédure : Par programmation exclure les marques de paragraphe lors de la création de plages'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], excluding paragraphs
- ranges, excluding paragraph marks in Word
- documents [Office development in Visual Studio], paragraph marks
- paragraphs, controlling structure
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ab8dc8e41983e6dd4bef8b3f7ba550853e32addd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847087"
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>Procédure : Par programmation exclure les marques de paragraphe lors de la création de plages
  Chaque fois que vous créez un objet <xref:Microsoft.Office.Interop.Word.Range> basé sur un paragraphe, tous les caractères non imprimables, comme les marques de paragraphe, sont inclus dans la plage. Vous pouvez insérer le texte d’un paragraphe source dans un paragraphe de destination. Si vous ne voulez pas fractionner le paragraphe de destination en paragraphes distincts, alors vous devez d’abord supprimer la marque de paragraphe du paragraphe source. De plus, dans la mesure où des informations de mise en forme sont stockées au sein de la marque de paragraphe, vous ne voulez peut-être pas l’inclure quand vous insérez la plage dans un paragraphe existant.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 L’exemple de procédure suivant déclare deux variables de chaîne, extrait le contenu des premier et deuxième paragraphes du document actif, puis intervertit leur contenu. L’exemple illustre ensuite la suppression de la marque de paragraphe de la plage à l’aide de la méthode <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> et l’insertion du texte à l’intérieur du paragraphe.  
  
## <a name="to-control-paragraph-structure-when-inserting-text"></a>Pour contrôler la structure de paragraphe lors de l’insertion de texte  
  
1.  Créez deux variables de plage pour les premier et deuxième paragraphes, puis extrayez leur contenu à l’aide de la propriété <xref:Microsoft.Office.Interop.Word.Range.Text%2A> .  
  
     L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document.  
  
     [!code-vb[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#27)]  
  
     L’exemple de code suivant peut être utilisé dans un complément VSTO au niveau de l’application. Ce code utilise le document actif.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#27)]  
  
2.  Affectez la propriété <xref:Microsoft.Office.Interop.Word.Range.Text%2A> , en intervertissant le texte des deux paragraphes.  
  
     [!code-vb[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#28)]
     [!code-csharp[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#28)]  
  
3.  Sélectionnez chaque plage une par une, puis effectuez une pause pour afficher les résultats dans une boîte de message.  
  
     [!code-vb[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#29)]
     [!code-csharp[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#29)]  
  
4.  Ajustez `firstRange` à l’aide de la méthode <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> pour que la marque de paragraphe ne fasse plus partie de `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#30)]
     [!code-csharp[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#30)]  
  
5.  Remplacez le reste du texte dans le premier paragraphe, en affectant une nouvelle chaîne à la propriété <xref:Microsoft.Office.Interop.Word.Range.Text%2A> de la plage.  
  
     [!code-vb[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#31)]
     [!code-csharp[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#31)]  
  
6.  Remplacez le texte dans `secondRange`, en incluant la marque de paragraphe.  
  
     [!code-vb[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#32)]
     [!code-csharp[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#32)]  
  
7.  Sélectionnez `firstRange` et effectuez une pause pour afficher les résultats dans une boîte de message, puis procédez de la même façon avec `secondRange`.  
  
     Étant donné que `firstRange` a été redéfini pour exclure la marque de paragraphe, la mise en forme d’origine du paragraphe est conservée. En revanche, une phrase a été insérée à la place de la marque de paragraphe dans `secondRange`, supprimant ainsi le paragraphe distinct.  
  
     [!code-vb[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#33)]
     [!code-csharp[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#33)]  
  
     Le contenu d’origine des deux plages a été enregistré sous forme de chaînes, donc vous pouvez rétablir le document à son état d’origine.  
  
8.  Réajuster `firstRange` pour inclure la marque de paragraphe à l’aide de la <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> méthode pour la position d’un caractère.  
  
     [!code-vb[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#34)]
     [!code-csharp[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#34)]  
  
9. Supprimez `secondRange`. Cette opération rétablit le paragraphe trois à sa position d’origine.  
  
     [!code-vb[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#35)]
     [!code-csharp[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#35)]  
  
10. Rétablissez le texte du paragraphe d’origine dans `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#36)]
     [!code-csharp[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#36)]  
  
11. Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Range> pour insérer le contenu du paragraphe deux d’origine après `firstRange`, puis sélectionnez `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#37)]
     [!code-csharp[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#37)]  
  
## <a name="document-level-customization-example"></a>Exemple de personnalisation au niveau du document  
  
### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>Pour contrôler la structure de paragraphe lors de l’insertion de texte dans des personnalisations au niveau du document  
  
1.  L’exemple suivant montre la méthode complète d’une personnalisation au niveau du document. Pour utiliser ce code, exécutez-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#26)]  
  
## <a name="vsto-add-in-example"></a>Exemple de complément VSTO  
  
### <a name="to-control-paragraph-structure-when-inserting-text-in-a-vsto-add-in"></a>Pour contrôler la structure de paragraphe lors de l’insertion de texte dans un composant logiciel complément VSTO  
  
1.  L’exemple suivant montre la méthode complète pour un composant logiciel complément VSTO. Pour utiliser ce code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#26)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Guide pratique pour Réduire des plages ou des sélections dans des documents par programmation](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Guide pratique pour Insérer du texte dans les documents Word par programmation](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Guide pratique pour Réinitialisation par programmation des plages dans des documents Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Guide pratique pour Définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
