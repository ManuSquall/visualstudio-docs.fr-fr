---
title: 'Comment : enregistrer des classeurs par programmation'
description: Enregistrez les classeurs Microsoft Excel par programmation sans modifier le chemin d’accès et enregistrer une copie d’un classeur sans modifier le classeur ouvert en mémoire.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4559d098a80a1dfd8f1d3f5c2c21cbebc992fcb7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828980"
---
# <a name="how-to-programmatically-save-workbooks"></a>Comment : enregistrer des classeurs par programmation
  Il existe plusieurs façons d'enregistrer un classeur. Vous pouvez le faire sans modifier le chemin d’accès. Si le classeur n'a pas été enregistré auparavant, vous devez l'enregistrer en spécifiant un chemin d'accès. Sans chemin d’accès explicite, Microsoft Office Excel enregistre le fichier dans le dossier actif avec le nom qui lui a été attribué lors de sa création. Vous pouvez également enregistrer une copie du classeur sans modifier le classeur ouvert en mémoire.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="save-a-workbook-without-changing-the-path"></a>Enregistrer un classeur sans modifier le chemin d’accès

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Pour enregistrer un classeur associé à une personnalisation au niveau du document

1. Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> de la classe `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet4":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Pour enregistrer le classeur actif dans un complément VSTO

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> pour enregistrer le classeur actif. Pour utiliser l’exemple de code suivant, exécutez-le dans la classe `ThisAddIn` dans un projet de complément VSTO pour Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet3":::

## <a name="save-a-workbook-with-a-new-path"></a>Enregistrer un classeur avec un nouveau chemin d’accès
 Vous pouvez enregistrer le classeur spécifié dans un nouvel emplacement ou avec un nouveau nom, en spécifiant éventuellement un format de fichier, un mot de passe, un mode d'accès, etc.

> [!NOTE]
> Vous souhaiterez peut-être affecter la valeur <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> **false** à la propriété avant d’enregistrer le classeur avec un nouveau chemin d’accès, car l’enregistrement dans certains formats nécessite une interaction. Si vous affectez à cette propriété la **valeur false** , Excel utilise toutes les valeurs par défaut.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Pour enregistrer un classeur associé à une personnalisation au niveau du document

1. Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> de la classe `ThisWorkbook` . Pour utiliser l'exemple de code suivant, exécutez-le dans la classe `ThisWorkbook`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet5":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Pour enregistrer le classeur actif dans un complément VSTO

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> pour enregistrer le classeur actif avec un nouveau chemin d’accès. Pour utiliser l’exemple de code suivant, exécutez-le dans la classe `ThisAddIn` dans un projet de complément VSTO pour Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet4":::

## <a name="save-a-copy-of-the-workbook"></a>Enregistrer une copie du classeur
 Vous pouvez enregistrer une copie du classeur dans un fichier sans modifier le classeur ouvert en mémoire. Cela est utile quand vous souhaitez créer une copie de sauvegarde sans modifier l'emplacement du classeur.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Pour enregistrer un classeur associé à une personnalisation au niveau du document

1. Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> de la classe `ThisWorkbook` . Pour utiliser l'exemple de code suivant, exécutez-le dans la classe `ThisWorkbook`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet6":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Pour enregistrer le classeur actif dans un complément VSTO

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> pour enregistrer une copie du classeur actif. Pour utiliser l’exemple de code suivant, exécutez-le dans la classe `ThisAddIn` dans un projet de complément VSTO pour Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet5":::

## <a name="robust-programming"></a>Programmation fiable
 L'annulation interactive d'une quelconque des méthodes qui enregistrent ou copient le classeur génère une erreur d'exécution dans votre code. Par exemple, si votre procédure appelle la <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> méthode, mais ne désactive pas les invites d’Excel, et que votre utilisateur clique sur **Annuler** lorsque vous y êtes invité, Excel déclenche une erreur d’exécution.

## <a name="see-also"></a>Voir aussi
- [Utiliser des classeurs](../vsto/working-with-workbooks.md)
- [Élément hôte de classeur](../vsto/workbook-host-item.md)
- [Comment : fermer des classeurs par programmation](../vsto/how-to-programmatically-close-workbooks.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
