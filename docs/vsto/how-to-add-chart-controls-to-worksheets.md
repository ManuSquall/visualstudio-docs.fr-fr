---
title: 'Comment : ajouter des contrôles Chart à des feuilles de calcul'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fdb1f738fe6e68f7470ae65e6ce08b2f3be0ef6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546235"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Comment : ajouter des contrôles Chart à des feuilles de calcul
  Vous pouvez ajouter des <xref:Microsoft.Office.Tools.Excel.Chart> contrôles à une feuille de calcul Microsoft Office Excel au moment du design et au moment de l’exécution dans des personnalisations au niveau du document. Vous pouvez également ajouter <xref:Microsoft.Office.Tools.Excel.Chart> des contrôles au moment de l’exécution dans des compléments VSTO.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Cette rubrique décrit les tâches suivantes :

- [Ajouter des contrôles Chart au moment du design](#designtime)

- [Ajouter des contrôles Chart au moment de l’exécution dans un projet au niveau du document](#runtimedoclevel)

- [Ajouter des contrôles Chart au moment de l’exécution dans un projet de complément VSTO](#runtimeaddin)

  Pour plus d’informations sur les <xref:Microsoft.Office.Tools.Excel.Chart> contrôles, consultez [Chart, contrôle](../vsto/chart-control.md).

## <a name="add-chart-controls-at-design-time"></a><a name="designtime"></a> Ajouter des contrôles Chart au moment du design
 Vous pouvez ajouter le contrôle <xref:Microsoft.Office.Tools.Excel.Chart> à votre feuille de calcul de la même manière que vous ajouteriez un graphique à partir de l'application.

> [!NOTE]
> Le <xref:Microsoft.Office.Tools.Excel.Chart> contrôle n’est pas disponible à partir de la **boîte à outils** ou de la fenêtre **sources de données** .

### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Pour ajouter un contrôle hôte Chart à une feuille de calcul dans Excel

1. Sous l’onglet **Insérer** , dans le groupe **graphiques** , cliquez sur **colonne**, cliquez sur une catégorie de graphiques, puis cliquez sur le type de graphique souhaité.

2. Dans la boîte de dialogue **Insérer un graphique** , cliquez sur **OK**.

3. Sous l’onglet **conception** , dans le groupe **données** , cliquez sur **Sélectionner des données**.

4. Dans la boîte de dialogue **Sélectionner une source de données** , cliquez dans la zone plage de **données** du **graphique** et effacez toutes les sélections par défaut.

5. Dans les **données de** la feuille de graphique, sélectionnez la plage de cellules qui contient les données du graphique (cellules **a5** à **D8**).

6. Dans la boîte de dialogue **Sélectionner une source de données** , cliquez sur **OK**.

## <a name="add-chart-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Ajouter des contrôles Chart au moment de l’exécution dans un projet au niveau du document
 Vous pouvez ajouter dynamiquement le contrôle <xref:Microsoft.Office.Tools.Excel.Chart> au moment de l'exécution. Les graphiques créés dynamiquement ne sont pas persistants dans le document en tant que contrôles hôtes lorsque le document est fermé. Pour plus d’informations, consultez [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Pour ajouter par programmation un contrôle Chart à une feuille de calcul

1. Dans le gestionnaire d'événements <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de `Sheet1`, insérez le code suivant pour ajouter le contrôle <xref:Microsoft.Office.Tools.Excel.Chart>

     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]

## <a name="add-chart-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Ajouter des contrôles Chart au moment de l’exécution dans un projet de complément VSTO
 Vous pouvez ajouter par programmation un contrôle <xref:Microsoft.Office.Tools.Excel.Chart> à une feuille de calcul ouverte dans un projet de complément VSTO. Pour plus d’informations, consultez [extension de documents Word et de classeurs Excel dans des compléments VSTO au moment](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)de l’exécution.

 Les contrôles Chart créés dynamiquement ne sont pas persistants dans la feuille de calcul en tant que contrôles hôtes lorsque la feuille de calcul est fermée. Pour plus d’informations, consultez [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Pour ajouter par programmation un contrôle Chart à une feuille de calcul

1. Le code suivant génère un élément hôte de feuille de calcul basé sur la feuille de calcul ouverte, puis ajoute un contrôle <xref:Microsoft.Office.Tools.Excel.Chart>.

     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple exige les éléments suivants :

- les données à représenter sur le graphique, stockées dans la plage comprenant les cellules A5 à D8 de la feuille de calcul.

## <a name="see-also"></a>Voir aussi
- [Étendre des documents Word et des classeurs Excel dans des compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Contrôles sur les documents Office](../vsto/controls-on-office-documents.md)
- [Chart, contrôle](../vsto/chart-control.md)
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
