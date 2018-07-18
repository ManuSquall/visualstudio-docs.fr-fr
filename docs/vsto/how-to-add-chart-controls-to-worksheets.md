---
title: 'Comment : ajouter des contrôles Chart aux feuilles de calcul'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 05fc2cafda3ed4aa0ff7756062c1cec0429ebc96
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548734"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Comment : ajouter des contrôles Chart aux feuilles de calcul
  Vous pouvez ajouter <xref:Microsoft.Office.Tools.Excel.Chart> contrôles à une feuille de calcul Microsoft Office Excel au moment du design et de l’exécution dans des personnalisations au niveau du document. Vous pouvez également ajouter <xref:Microsoft.Office.Tools.Excel.Chart> contrôles lors de l’exécution dans des Compléments VSTO.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Cette rubrique décrit les tâches suivantes :  
  
-   [Ajouter des contrôles Chart au moment du design](#designtime)  
  
-   [Ajouter des contrôles Chart au moment de l’exécution dans un projet au niveau du document](#runtimedoclevel)  
  
-   [Ajouter des contrôles Chart au moment de l’exécution dans un projet de complément VSTO](#runtimeaddin)  
  
 Pour plus d’informations sur <xref:Microsoft.Office.Tools.Excel.Chart> contrôles, consultez [graphique](../vsto/chart-control.md).  
  
##  <a name="designtime"></a> Ajouter des contrôles Chart au moment du design  
 Vous pouvez ajouter le contrôle <xref:Microsoft.Office.Tools.Excel.Chart> à votre feuille de calcul de la même manière que vous ajouteriez un graphique à partir de l'application.  
  
> [!NOTE]  
>  Le <xref:Microsoft.Office.Tools.Excel.Chart> contrôle n’est pas disponible à partir de la **boîte à outils** ou **des Sources de données** fenêtre.  
  
### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Pour ajouter un contrôle hôte Chart à une feuille de calcul dans Excel  
  
1.  Sur le **insérer** sous l’onglet du **graphiques** , cliquez sur **colonne**et cliquez sur une catégorie de graphiques, puis cliquez sur le type de graphique souhaité.  
  
2.  Dans le **insérer un graphique** boîte de dialogue, cliquez sur **OK**.  
  
3.  Sur le **conception** sous l’onglet du **données** , cliquez sur **sélectionner les données**.  
  
4.  Dans le **sélectionner une Source de données** boîte de dialogue, cliquez dans le **graphique** **plage de données** zone, puis désactivez toutes les sélections par défaut.  
  
5.  Dans le **les données de graphique** feuille, sélectionnez la plage de cellules qui contient les données pour le graphique (cellules **A5** via **D8**).  
  
6.  Dans le **sélectionner une Source de données** boîte de dialogue, cliquez sur **OK**.  
  
##  <a name="runtimedoclevel"></a> Ajouter des contrôles chart au moment de l’exécution dans un projet au niveau du document  
 Vous pouvez ajouter la <xref:Microsoft.Office.Tools.Excel.Chart> contrôle dynamiquement au moment de l’exécution. Les graphiques créés dynamiquement ne sont pas persistants dans le document en tant que contrôles hôtes lorsque le document est fermé. Pour plus d’informations, consultez [ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Pour ajouter par programmation un contrôle Chart à une feuille de calcul  
  
1.  Dans le gestionnaire d'événements <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de `Sheet1`, insérez le code suivant pour ajouter le contrôle <xref:Microsoft.Office.Tools.Excel.Chart>  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> Ajouter des contrôles chart au moment de l’exécution dans un projet de complément VSTO  
 Vous pouvez ajouter par programmation un contrôle <xref:Microsoft.Office.Tools.Excel.Chart> à une feuille de calcul ouverte dans un projet de complément VSTO. Pour plus d’informations, consultez [documents Word d’étendre et classeurs Excel dans des Compléments VSTO lors de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Les contrôles Chart créés dynamiquement ne sont pas persistants dans la feuille de calcul en tant que contrôles hôtes lorsque la feuille de calcul est fermée. Pour plus d’informations, consultez [ajouter des contrôles à Office documents lors de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Pour ajouter par programmation un contrôle Chart à une feuille de calcul  
  
1.  Le code suivant génère un élément hôte de feuille de calcul basé sur la feuille de calcul ouverte, puis ajoute un contrôle <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple exige les éléments suivants :  
  
-   les données à représenter sur le graphique, stockées dans la plage comprenant les cellules A5 à D8 de la feuille de calcul.  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre des documents Word et classeurs Excel dans des Compléments VSTO lors de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)   
 [Chart (contrôle)](../vsto/chart-control.md)   
 [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Éléments hôtes et vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Lier des données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  