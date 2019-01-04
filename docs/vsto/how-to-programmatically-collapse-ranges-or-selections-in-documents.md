---
title: 'Procédure : Réduire des plages ou des sélections dans des documents par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- selections, collapsing
- documents [Office development in Visual Studio], collapsing ranges
- collapsing selections
- ranges, collapsing
- collapsing ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d26a664a6d66c81a7409759478eb8c9de120964d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859066"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Procédure : Réduire des plages ou des sélections dans des documents par programmation
  Si vous travaillez avec un objet <xref:Microsoft.Office.Interop.Word.Range> ou <xref:Microsoft.Office.Interop.Word.Selection> , vous pouvez remplacer la sélection par un point d’insertion avant d’insérer du texte, afin d’éviter de remplacer le texte existant. À la fois le <xref:Microsoft.Office.Interop.Word.Range> et <xref:Microsoft.Office.Interop.Word.Selection> objets ont une méthode Collapse, qui utilise le <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> valeurs d’énumération :  
  
- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> réduit la sélection au début de la sélection. Il s’agit de la valeur par défaut si vous ne spécifiez pas de valeur d’énumération.  
  
- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> réduit la sélection à la fin de la sélection.  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-collapse-a-range-and-insert-new-text"></a>Pour réduire une plage et insérer un nouveau texte  
  
1. Créez un objet <xref:Microsoft.Office.Interop.Word.Range> constitué du premier paragraphe du document.  
  
    Vous pouvez utiliser l’exemple de code suivant dans une personnalisation au niveau du document.  
  
    [!code-vb[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#46)]  
  
    L'exemple de code suivant peut être utilisé dans un complément VSTO. Ce code utilise le document actif.  
  
    [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#46)]  
  
2. Utilisez la valeur d’énumération <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> pour réduire la plage.  
  
    [!code-vb[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#47)]
    [!code-csharp[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#47)]  
  
3. Insérez le nouveau texte.  
  
    [!code-vb[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#48)]
    [!code-csharp[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#48)]  
  
4. Sélectionnez le contrôle <xref:Microsoft.Office.Interop.Word.Range>.  
  
    [!code-vb[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#49)]
    [!code-csharp[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#49)]  
  
   Si vous utilisez la valeur d’énumération <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> , le texte est inséré au début du paragraphe suivant.  
  
   [!code-vb[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#50)]
   [!code-csharp[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#50)]  
  
   Vous pourriez vous attendre à ce que l’insertion d’une nouvelle phrase se fasse avant la marque de paragraphe, mais ce n’est pas le cas, car celle-ci est incluse dans la plage d’origine. Pour plus d'informations, voir [Procédure : Exclure les marques de paragraphe par programmation lors de la création de plages](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).  
  
## <a name="document-level-customization-example"></a>Exemple de personnalisation au niveau du document  
  
### <a name="to-collapse-a-range-in-a-document-level-customization"></a>Pour réduire une plage dans une personnalisation au niveau du document  
  
1.  L’exemple suivant affiche la méthode complète correspondant à la personnalisation au niveau du document. Pour utiliser ce code, exécutez-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#45)]  
  
## <a name="vsto-add-in-example"></a>Exemple de complément VSTO  
  
### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>Pour réduire une plage dans un complément, VSTO  
  
1.  L’exemple suivant montre la méthode complète pour un composant logiciel complément VSTO. Pour utiliser ce code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#45)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Insérer du texte dans les documents Word par programmation](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Guide pratique pour Définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Guide pratique pour Récupérer par programme des caractères de début et de fin dans les plages](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Guide pratique pour Par programmation exclure les marques de paragraphe lors de la création de plages](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Guide pratique pour Étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Guide pratique pour Réinitialisation par programmation des plages dans des documents Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)  
